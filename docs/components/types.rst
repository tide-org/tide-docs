Types
=====

The config file has a set of config commands that make up a config_command_item.

these config commands have a series of steps, or config_command_actions, or just command_actions.

Each command_action has a type (as per the /actions path.

A command_action is a single step in a config_command_item.

A command_action that runs against the process is just a command.

relationship is:

config - command - action

---

buffers may have one or more filter

filters can apply to all output or just one buffer


events:

event_input_args - used from events in config (input_args) - eg. do_buffer_diff - that is run from a buffer event
command_args - used from commands (internal) for additional data for the command that is run from an event(lines, command string, etc.) - eg. set_remote_target
could standardise command_args to to use a buffer


event flows:

buffer:
user action - > config -> command -> buffer -> buffer_event (event_input_args)

user_action:
user action -> config -> command -> config event -> command event (command_args)

event types:

buffer updates:
- before_buffer
- after_buffer

user actions:
- before_startup
- afer_startup
- before_command
- after_command



