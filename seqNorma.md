# Sequelize-Normalization

There are three standard associations: One-To-One, One-To-Many and Many-To-Many.
We first must make the model for example:`sequelize.define('A',{//defineDataTypes})`.

## Overview

### Sequelize provides *four* types of associations that should be combined to create them:
- `HasOne`: `A.hasOne(B)`: One-To-One relationship exists between A and B, with the foreign key being defined in the target model (B).
- `BelongsTo`: `A.belognsTo(B)`: One-To-One relationship, with the foreign key being defined in the source model (A).
- `HasMany`: `A.hasMany(B)`: One-To-Many relationship, with the foreign key being defined in the target model (B).
- `BelongsToMany`: `A.belongsToMany(B, { through: 'C' })`: Many-To-Many relationship exists between A and B, using table C as junction table, which will have the foreign keys (aId and bId, for example). 
Sequelize will automatically create this model C (unless it already exists) and define the appropriate foreign keys on it.

#### In previous example, we call A the **source** model and B the **target** model.

### Let's summarize:
- To create 1-1 relationship: the `hasOne` and `belongsTo` associations are used together.
- To create 1-many relationship: `hasMany` and `belongsTo` associations are used together.
- To create many-many relationship: two `belongsToMany` calls are used together.

## One-One Relationships
### Two models: `Foo` and `Bar`.
`Foo.hasOne(Bar); Bar.belongsTo(Foo);`: Sequelize knows that a `fooId` column must be added to `Bar`.

## One-To-Many relationships
### Two models: `Team` and `Player`. 
`Team.hasMany(Player); Player.belongsTo(Team);`: Team has many Players, while each Player belongs to a single Team.

## Many-To-Many relationships
### Two models: `Movie` and `Actor`.
> const Movie = sequelize.define('Movie', { name: DataTypes.STRING });
> 
> const Actor = sequelize.define('Actor', { name: DataTypes.STRING });
> 
> Movie.belongsToMany(Actor, { through: 'ActorMovies' });
> 
> Actor.belongsToMany(Movie, { through: 'ActorMovies' });

### Sequelize will automatically create the ActorMovies model which will act as the junction model. I can create it to.

## Notes
### There are three ways to specify a different name for the foreign key:
- By providing the foreign key name directly.
- By defining an Alias.
- By doing both things.
### There are some special methods/mixins will be added to instances after calling `hasOne`, `belognsTo`, `hasMany` and `belongsToMany` functions.
### Why associations are defined in pairs?
Because we need the source and target models to know about existence of our association.
### Sequelize allows us to define an association that uses another field, instead of the primary key field, to establish the association.

[References](https://sequelize.org/docs/v6/core-concepts/assocs/)
[Home Page](./README.md)
