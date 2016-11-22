# Pinit

Add a bookmark to [Pinboard](https://pinboard.in/). The URL may be given via
standard input, as an argument, or copied from the clipboard.

I frequently want to bookmark a URL in Pinboard while not logged in. Maybe I'm
in my primary browser but my Pinboard cookie has expired. Maybe I'm in a
[disposable browser](https://github.com/pigmonkey/firewarden/) where I'm not
logged in to any accounts. Maybe I'm not in a browser at all, but someone sent
me a link via email or a chat application. By binding this script to a
keystroke, I can easily add a bookmark in any of these scenarios.

## Requirements

* [xdotool](http://semicomplete.com/projects/xdotool) is used to get the name
  of the window currently under the mouse pointer (to be used as the default
  bookmark name).
* [xclip](https://github.com/astrand/xclip) is used to get the URL out of the
  clipboard.

## Setup

1. [Buy a Pinboard account](https://pinboard.in/signup/).
2. Export your Pinboard user name `$PINBOARD_USER` and your Pinboard API key as `$PINBOARD_KEY`.
3. There is no step 3.

## Usage

I bind the script via [sxhkd](https://github.com/baskerville/sxhkd). The script
uses interactive input, so rather than calling it directly, I execute it via a
terminal (in my case [termite](https://github.com/thestinger/termite), but any
will do).

    # ~/.config/sxhkd/sxhkdrc
    super + d
        termite --title pinit -e ~/bin/pinit.sh

I use the [i3](https://i3wm.org/) window manager. Because I gave the terminal a
window title, I can tell i3 to float that window.

    # ~/.config/i3/config
    for_window [title="pinit"] floating enable

Now when I want to bookmark a URL I'll copy it to my clipboard and hit `super + d`.
