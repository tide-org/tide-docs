Vgdb guide
==========

# start Vgdb

`:Vgdb`

# run a command

`:Vgc`

# connect to a remote target

`:Vgc target remote localhost:9999`

# run application and break at entrypoint (sets a breakpoint)

`:Vgrte`

# display registers window

`:Vgreg`


# to step into an instruction:

`:VgRunConfigCommand stepi`

# to continue to end:

`:VgRunConfigCommand continue`

# to show disassembly:

`:Vgdis`


# Config description:

commands can have the following types:

type: 'command_with_match'
type: 'command'
type: 'vim_command'
type: 'python_command'

variables can have the following types:

type: 'python_and_vim'
type: 'python'
type: 'vim'

events can be of the following types:

before_spawn:
after_spawn:
before_config_command:
after_config_command:
before_command:
after_command:
before_buffer_update:
after_buffer_update:

event types can be of the following:

type: 'vim'
type: 'python'

event types should have the following elements:

run_for: - this is only relevant to commands
type: - described above
function: the name of the function to run, either python or vim


