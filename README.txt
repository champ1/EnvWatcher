This is EnvWatcher.
===================
A project by Simon Heisterkamp (heisterkamp@nbi.dk)

The project has just been launched and is not functional yet.

The intention is the following:

One sources a setup script like this: source EnvWatcher/setup.sh

after that the function env-watcher is available. It can be used like
this:

At any point one can call:

$ envwatcher record MyName 
started Mon 30 May 2011 11:31:44 CEST $

After that any changes that are made to the local variables, environment
variables or alias are recorded.

stop recording by calling

$ envwatcher stop MyName 
Environment record saved to $ENV_WATCHER_SESSION/MyName.env

The EnvWatcher makes a diff of the environments before and after the
recording period, watching for new variables, removed variables, changed
variables, prepended path-like variables. At any later time the change
can be undone by calling:

$ envwatcher revert MyName
Environment change reverted from file $ENV_WATCHER_SESSION/MyName.env 

A revert can also be issued to a currently recording session, thus
allowing things like $ envwatcher record Clean # at the start of a
session $ envwathcer revert Clean # at any later time.

Another use mode is to call "save":

$ envwatcher save MyState

This is less clever and will save the current state without any checks.
The state can be recovered by calling

$ envwacher revert MyState

Just like in the previous case.