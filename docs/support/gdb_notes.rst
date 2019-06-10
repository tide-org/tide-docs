for debugging c applications that were built on mac as a MachO binary:

brew install https://raw.githubusercontent.com/timotheecour/homebrew-timutil/master/gdb_tim.rb

as gdb needs to be codesigned (for local work) you should run vim as sudo with environment variables:

e.g.

sudo -E vim

for debugging a remote linux target:

http://tomszilagyi.github.io/2018/03/Remote-gdb-with-stl-pp

brew install gdb --with-all-targets


to switch:

for remote:

brew unlink gdb && brew link --overwrite gdb

for local:

brew unlink gdb_tim && brew link --overwrite gdb_tim


Determining the correct version for remote debugging:
=====================================================

If you get the following error in the vgdb_session.log file:

--- 2019-06-10 10:15:48.558387 ---
target remote localhost:9999
&"target remote localhost:9999\n"
~"Remote debugging using localhost:9999\n"
&"warning: A handler for the OS ABI \"GNU/Linux\" is not built into this configuration\nof GDB.  Attempting to continue with the default i386:x86-64 settings.\n"
&"\n"
&"warning: Architecture rejected target-supplied description\n"
=tsv-created,name="trace_timestamp",initial="0"\n
=thread-group-started,id="i1",pid="12"
~"Reading /binaries/hello_linux from remote target...\n"
&"warning: File transfers from remote targets can be slow. Use \"set sysroot\" to access files locally instead.\n"
&"warning: \"target:/binaries/hello_linux\": not in executable format: file format not recognized\n"
~"Reading /binaries/hello_linux from remote target...\n"
&"warning: `target:/binaries/hello_linux': can't read symbols: file format not recognized.\n"
=thread-created,id="1",group-id="i1"
=thread-group-exited,id="i1"
&"Remote register badly formatted: T0506:0000000000000000;07:80edffffff7f0000;10:307cddf7ff7f0000;thread:pc.c;core:0;\n"
&"here: 00000000;07:80edffffff7f0000;10:307cddf7ff7f0000;thread:pc.c;core:0;\n"
^error,msg="Remote register badly formatted: T0506:0000000000000000;07:80edffffff7f0000;10:307cddf7ff7f0000;thread:pc.c;core:0;\nhere: 00000000;07:80edffffff7f0000;10:307cddf7ff7f0000;thread:pc.c;core:0;"

``

The version of gdb you are running locally on your Mac does not support GNU Linux emote debugging.
