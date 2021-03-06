Terminal
--------
I use a few dotfiles and `z` on macOS and bash on Windows 10. You should too.

### Dotfiles ###

I really like [Paul Irish’s dotfiles][irish], but you kind of add a bunch of things without knowing what you’re doing. I’m currently using it with some modifications on macOS, but I wouldn’t know which part of it to recommend to you.

I’ve only included the dotfile settings I use across both macOS and bash on Windows 10, since my idiosyncracies aren’t useful to anyone else.

#### Installation ####

Adding aliases and dotfiles is pretty easy.

`.bashrc` is what happens when you load your terminal. So you’ll want to add your aliases on load.

Rather than write directly to `.bashrc`, making your own dotfiles and importing them from `.bashrc` is cleaner.

Create or copy a dotfile like `~/.myaliases`. Add some aliases to it.

Afterwards, load it from `.bashrc` like so:

```sh
if [ -f ~/.myaliases ]; then
    . ~/.myaliases
fi
```

It tells bash to load the file if it exists.

This way, the only thing I add to `.bashrc` is this:

```sh
if [ -f ~/.myaliases ]; then
    . ~/.myaliases
fi

if [ -f ~/.myenv ]; then
    . ~/.myenv
fi

if [ -f ~/.myfunctions ]; then
    . ~/.myfunctions
fi

if [ -f ~/.paulirishaliases ]; then
    . ~/.paulirishaliases
fi

if [ -f ~/z.sh ]; then
    . ~/z.sh
fi
```

### `.myfunctions` ###

Check out [`.myfunctions`][myfunctions] in this folder for my secret recipes that will greatly improve your day-to-day scripting.

I haven’t included everything, but it sure as heck is more orderly than my own dotfile.

### z.sh ###

I don't know how people use terminals without [`z`][z].

Installing z is easy:

* Download `z.sh`
* Put it wherever, like `~/`
* Load it from `.bashrc` with `. ~/z.sh`

### macOS ###

#### Theme ####

##### Solarized Dark #####

Before, I used [Solarized Dark][] by tomislav.

With a custom config:

* 12pt font size vs 11pt
* #FFF font colour vs dark grey
* Blinking text disabled

##### Dracula #####

Right now, I’m using [Dracula][] to great effect.

![Dracula terminal theme][dracula-screenshot]


[irish]: https://github.com/paulirish/dotfiles
[myfunctions]: https://github.com/ndarville/style/blob/master/terminal/dotfiles/.myfunctions
[z]: https://github.com/rupa/z
[solarized dark]: https://github.com/tomislav/osx-terminal.app-colors-solarized
[dracula]: https://draculatheme.com/terminal/
[dracula-screenshot]: https://raw.githubusercontent.com/ndarville/style/master/terminal/dracula.png
