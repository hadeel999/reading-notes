# Access Control (ACL)

## What is Role Based Access Control (RBAC) ?
RBAC is the idea of assigning system access to users based on their role in an organization.

## Why do we care?
- Case in point: the 2017 Verizon Data Breach Investigations Report found that 81 percent of hacking-related breaches involved compromised credentials.
- The number of possible permutations of access settings in such a small environment is huge.

### Some alternatives of RBAC:
- Access control lists (ACL).
- Attribute-based access control (ABAC).

#### RBAC arguably offers a more simplified and manageable approach.

## RBAC implementation
Five steps:
1. Inventory your systems: What resources you have for which you need to control access.
2. Analyze your workforce and create roles: Group your workforce members into roles with common access needs. 
3. Assign people to roles: Which role(s) each employee belongs in.
4. Never make one-off changes: Resist any temptation to make a one-off change for an employee with unusual needs.
5. Audit: Periodically review your roles, the employees assigned to them, and the access permitted for each.

## Three primary rules defined for RBAC.
1. Role assignment: A subject can exercise a permission only if the subject has selected or been assigned a role.
2. Role authorization: A subject's active role must be authorized for the subject. 
3. Permission authorization: A subject can exercise a permission only if the permission is authorized for the subject's active role.

### Difference between authentication and authorization:

>> Authentication is the process of verifying who a user is.
>>
>> Authorization is the process of verifying what they have access to.

## References:
[5 steps to RBAC](https://www.csoonline.com/article/3060780/5-steps-to-simple-role-based-access-control.html)
[wiki - RBAC](https://en.wikipedia.org/wiki/Role-based_access_control)


### [Home Page](./README.md)
