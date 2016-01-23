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

```
init() {
    this.moduleLoader.registerAction({
        moduleName: this.moduleName,
        name: 'my-action',
        matcher: 'myActionMatcher',
        callback: 'myActionCallback'
    });
}
```

- `name`: Name of the action
- `matcher`: Function to distinguish if the action should be activated. Takes a string as input for comparison. Can also be a string, referring to a function inside the module class.
- `callback`: Function to be call. Can also be a string, referring to a function inside the module class.

## Tasks

Tasks are executed recurring, much like cron jobs. A task usually is registered inside the `init()` function
of a module.

```
init() {
    this.moduleLoader.registerTask({
        moduleName: this.moduleName,
        name: 'my-task',
        interval: '*/5 * * * *',
        callback: 'myTaskCallback'
    });
}
```

- `name`: Name of the task
- `interval`: Interval, the task should be run. Can be a cron-like string or object. See [node-schedule documentation](https://github.com/node-schedule/node-schedule) for more information.
- `callback`: Function to be called. Can also be a string, referring to a function inside the module class.

## Commands

Commands can be called via `./bin/bot <my-command>`.

```
init() {
    this.moduleLoader.registerCommand({
        moduleName: this.moduleName,
        name: 'my-command',
        description: 'The description of my command',
        options: [
            ['-l, --list', 'List all super villains from Batman'],
        ],
        callback: 'myCommandCallback'
    });
}
```

- `name`: Name of the command
- `description`: Description of the command
- `options`: Array of options for the command. See [commander.js documentation](https://github.com/tj/commander.js) for more information.
- `callback`: Function to be called. Can also be a string, referring to a function inside the module class.

## About
„We build it" -- [ANIMAL](http://animal.at)
