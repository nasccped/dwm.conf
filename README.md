dwm conf
========

Welcome to my personal config for DWM Window Manager 🪟

> [!NOTE]
>
> I'm not the owner of this projet. It was forked from
> https://git.suckless.org/dwm and you can find the original readme
> (`README.old.txt`) and the license (`LICENSE`) as well.
>
> This page bellow was written by me. Its documents the requirements,
> cloning and installing the program (and changes that I've done).

## What's DWM?

[DWM](https://dwm.suckless.org/) is a dynamic window manager for X.
It can managed windows in different ways such as **monocle**,
**tiled** and **floating**.

It works the almost the same as
[BSPWM](https://github.com/baskerville/bspwm),
[FVWM](https://www.fvwm.org/) and others but I like this one because
of its simplicity and no RAM _eating_.

## Let's install it

### Requirements

DWM is built under the Xorg programs, so you'll need its libraries
and commands:

- libx11
- libxft
- libxinerama
- xorg
- xorg-xinit

I'm currently using the `Terminus:Bold` font, so you'll need it too:

- terminus-font

> [!NOTE]
>
> You can install all this stuff by using your package manager.
> Unfortunately, stable distros can suffer from outdated packages
> (I'm currently using Arch ~btw~). If it's your case, you'll
> probably need to handle a secundary package manager or build some
> _ deps._ from source 😞
>
> ---
>
> It's obvious but you'll also need the C compiler (`gcc`) and the
> make compiler tool (`make`)!
>
> ---
>
> I'm using:
> - `st - Suckless Terminal` _(`Shift` + `ModKey` + `Return`)_
> - `dmenu` _(`ModKey` + `P`)_
>
> It's recommended that you also have (or at least some good
> substitute such as `alacritty` and `rofi` - **YOU'LL NEED TO CHANGE
> THE `config.h` file to set the new apps**).

### Cloning

1. Clone with git + `cd` + remove git directory:

```sh
git clone https://github.com/nasccped/dwm.conf && \
cd dwm.conf && \
rm -rf .git/
```

2. Install the dependencies listed at [requirements](#requirements)

3. Use the `Makefile` + `gcc` to compile the program:

```sh
make clean && sudo make install # you should be a super user + set your password
```

4. Add this to your `.xinitrc` (if it doesn't exists, create one):

```txt
exec dwm
```

And now, you can run `startx` at your TTY and see the actual program!

### Some good tips

#### Display

This can differ from computer to computer, so, follow these steps
wisely:

1. Open your dwm client (it's import to have a terminal emulator
   already setted):
```sh
startx
```

2. Open your terminal emulator (`Shift` + `ModKey` + `Return` by
   default) and run the following command to see all available
   display outputs:
```sh
xrandr
```

3. Find the mode that works for you (`1920x1080` res. + `60Hz` rate
   in my case)

4. Set xrandr mode in `.xinitrc` before calling `dwm`:

```txt
# the --output flag should receive the current screen being displayed
# (it can differ from computer to computer)
xrandr --output Virtual-1 --mode 1920x1080 --rate 60
```

#### Keyboard layout

The keyboard layout defined at Xorg client is different from the TTY
layout. You'll need to set your keyboard-layout to Xorg client in
`.xinitrc` too (`br-abnt2` in my case):

```txt
stxkbmap -layout br -variant abnt2
```

> [!TIP]
>
> If you don't know yours, you can google it (it's common to all
> computers from the same country follow the same keyboard layout) 😉

## Changes that I've made

- use `Win` as **ModKey**
- use `alwayscenter` patch (center windows when floating)
- use `splitstatus` for status root name spliting (mid + right). My
  personal rootname config (in `.xinitrc`) is:
```txt
while xsetroot -name "`date '+%H:%M'`;`date '+| %A | %b %d, %Y'` "
do
  sleep 60
done &
exec dwm
```
