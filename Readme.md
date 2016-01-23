# Example module for ANIMAL bot.
This repository will serve as a simple example on how to extent the [ANIMAL bot](https://github.com/AnimalDesign/bot).

## Structure
ANIMAL bot modules are expected to have the following structure:

```
server/modules
  |- <modulename>
    |- models (optional)
    |- tests (optional)
    |- config.json.dist (optional)
    |- module.js
    |- package.json
    |- readme.md
```

- `models`: Contains information about database structure and relations.
- `tests`: _not yet implemented, reserved for future usage._
- `config.json.dist`: Distributed configuration file, containing default/available configuration options.
- `module.js`: The main logic of a module. Extends `baseModule`
- `package.json`: Contains the package description and dependencies.
- `readme.md`: Just explains the problem, a module is going to solve, how to set it up and so on.

> **Note:** A module can be deactivated simply by renaming its `module.js` file.

## Actions
## Tasks
## Commands
## Events
**Not yet implemented.**

## About
„We build it" -- [ANIMAL](http://animal.at)
