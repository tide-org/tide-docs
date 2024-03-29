GDB commands (reference guide)
==============================

ref: https://sourceware.org/gdb/onlinedocs/gdb/Symbols.html


getting the line and file of the current breakpoint

e.g.

(gdb) info line
Line 9 of "hello.c" starts at address 0x40054d <main+39> and ends at 0x40054f.

setting a breakpoint based on file name and line number:

e.g.

gdb> break /Full/path/to/service.cpp:45


getting a list of all variables in current context:

e.g.

info locals


getting a list of all functions:

e.g.

info functions

can take regex:

e.g.

info functions regex

getting all global/local variables:

info variables

getting all variables on the stack frame:

info args


links on variables:

https://stackoverflow.com/questions/6261392/printing-all-global-variables-local-variables

https://sourceware.org/gdb/onlinedocs/gdb/Variables.html


specifying source directories:

https://sourceware.org/gdb/onlinedocs/gdb/Source-Path.html


backtrace also has line numbers:

e.g.

backtrace full

also useful for getting source info:

at current breakpoint:

info source

and

all source files:

info sources


get symbols for a file:

e.g.

maint print symbols -source main.c

a good way to separate external libraries to linked files:

maint info symtabs

the objfile will match the binary being debugged for locally linked files

get a list of lines in each file that breakpoints can be set at:

for all source files:

maint info line-table

or for just one file:

maint info line-table main.c


setting source paths:

https://sourceware.org/gdb/onlinedocs/gdb/Source-Path.html

You can configure a default source path substitution rule by configuring GDB with the ‘--with-relocated-sources=dir’ option. The dir should be the name of a directory under GDB’s configured prefix (set with ‘--prefix’ or ‘--exec-prefix’), and directory names in debug information under dir will be adjusted automatically if the installed GDB is moved to a new location. This is useful if GDB, libraries or executables with debug information and corresponding source code are being moved together.


# Startup process:

after startup:

(gdb) set directories ./tests/binaries/c_test

then

(gdb) info source
Current source file is main.c
Compilation directory is /binaries/mac_test
Located in /work/tests/binaries/c_test/main.c
Contains 8 lines.
Source language is c.
Producer is GNU C11 5.5.0 20171010 -mtune=generic -march=x86-64 -g -fstack-protector-strong.
Compiled with DWARF 2 debugging format.
Does not include preprocessor macro info.

use 'Located in' line and 'Contains n lines.' lines to verify the source file is correct.

Then display the source file in the primary window.

backtrace - can be used to give the current line number as #0

valid line numbers to set breakpoints can be determined with:

maint info line-table main.c

bash line to run test binary: bin/dev-environment ./tests/binaries/c_test/c_test


# gdb version - needs to be 8.2.1


## Working config at:

plugins/test_c

start:

:Vgdb

set breakpoint to line 6:

:VgRunConfigCommand set_breakpoint

run to breakpoint:

:VgRunConfigCommand run

step through lines:

:VgRunConfigCommand step




