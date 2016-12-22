Using C++ in Sublime Text 3
===========================

Windows
-------
Download `codeblocks-XX.YYmingw-setup.exe` from [Code::Blocks][].

### Supporting `cin` ###

Sublime Text 3 doesn’t support interactive input streams by default, so we have to work around it.

Save `C++.sublime-build` to `%APPDATA%\Sublime Text 3\Packages\User`. (h/t [Abhinav Kumar][])

In Sublime Text, go to `Tools -> Build System` and select the new “C++” build system.

Then type `Ctrl + Shift + B` and select “C++ - Run”, which opens an interactive terminal.

With the current configuration, the terminal window shuts down as soon as you enter the last input, unfortunately.


[code::blocks]: http://www.codeblocks.org/downloads/binaries
[abhinav kumar]: https://www.quora.com/Is-there-a-way-to-compile-and-run-C++-in-Sublime-Text?share=1
