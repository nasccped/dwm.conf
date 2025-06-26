dwm conf
========

Welcome to my personal config for DWM Window Manager 🪟

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

## Changes that I've made

- use `Win` as **ModKey**
