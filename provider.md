# Context API - Behaviors

## Globally Accessible
The state of our snackbars (which ones are visible) can be localized to a single centralized component. That same centralized component can be responsible for rendering them. There’s really no need for another component somewhere in the tree to hook into that state (at least not in our use-case).

However, the management of that state (adding, removing) needs to be globally accessible.

```
export const SnackBarContext = createContext()

export function SnackBarProvider({ children }) {
  const [alerts, setAlerts] = useState([])

  return (
    <SnackBarContext.Provider value={{ setAlerts }}>
      {children}
      {alerts.map((alert) => <SnackBar key={alert}>{alert}</SnackBar>)}
    </SnackBarContext.Provider>
  )
}

```

Our context provider is now responsible for both displaying the local state of the snackbars (we call them alerts), and for exposing an API for globally managing them.

The other half of the puzzle is we now need a consumer for this provider. It turns out that our custom hook from before is nothing more than a small wrapper around the `useContext` internal React hook, which consumes our new context.

```
import { useContext } from 'react'

import { SnackBarContext } from 'components/snack-bar-provider'

const useSnackBars = () => useContext(SnackBarContext)

export default useSnackBars

```

This is not perfect yet though. Our provider exposes the state mutator `setAlerts` directly, but we need something much higher level. We don’t want our components fumbling around with how to add an alert without destroying existing ones, and so on. Think of `setAlerts` as a private method, and we need to expose a public method that abstracts away the noise.

## Higher Level API & Behaviour

```
export const SnackBarContext = createContext()

const AUTO_DISMISS = 5000

export function SnackBarProvider({ children }) {
  const [alerts, setAlerts] = useState([])
  
  const activeAlertIds = alerts.join(',')
  useEffect(() => {
    if (activeAlertIds.length > 0) {
      const timer = setTimeout(() => setAlerts((alerts) => alerts.slice(0, alerts.length - 1)), AUTO_DISMISS)
      return () => clearTimeout(timer)
    }
  }, [activeAlertIds])

  const addAlert = (alert) => setAlerts((alerts) => [alert, ...alerts])

  const value = { addAlert }
    
  return (
    <SnackBarContext.Provider value={value}>
      {children}
      {alerts.map((alert) => <SnackBar key={alert}>{alert}</SnackBar>)}
    </SnackBarContext.Provider>
  )
}
```

Our provider now exposes a new function called `addAlert`. This function uses the local state mutator `useState` to properly append a new alert without destroying existing ones. You could do more fancy things here: de-dup alerts, assign unique IDs to alerts so that we can also expose a `removeAlert` function that makes use of those IDs, and so on. But we’re going to keep it simple.

Most importantly perhaps is that we now make use of `useEffect` to display each alert for 5 seconds on the screen.

When a new alert is added, the component is re-rendered, and the effect is executed. In that effect, a timer is kicked off to remove the oldest living alert after a delay. This timer is a side-effect of that render.

When an alert is removed as a result of the above timer expiring, this component is re-rendered with the new state of `alerts`. Just as before, the side-effect will run, creating a new timer. Before doing that though, it will clean up the side-effect from the previous render (by clearing the timer). The timer is essentially restarted (by deleting the old timer and creating a new one).

This render and side-effect process repeats until `alerts` /`activeAlertIds` is empty. This is our base case if you want to think of this recursively.

## References:

[Hooks and Context example](https://medium.com/swlh/snackbars-in-react-an-exercise-in-hooks-and-context-299b43fd2a2b)

[Awesome React Context links](https://github.com/diegohaz/awesome-react-context)

### [Home Page](./README.md)
