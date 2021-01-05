# Fixing Logitech MX Keys for Mac

## The problem

Logitech makes two flavours of its "MX Keys" keyboard series. First one is the
multi-system labeled keys, targeted to any system. Later the "MX Keys for Mac"
flavour was introduced, with Mac-only labeled keys, and lighter grey colour.

I was given one of the latter, with Spanish layout, which, so far seemed
to work fine until I noticed the key under Escape ("ºª\") and the key
next to left Shift ("<>") were swapped:

![Image of swapped keys](https://raw.githubusercontent.com/mones/fix-mx-keys-for-mac/main/swapped_keys.png)


## The research

After some googling finally found I was not alone in the dark, and other
users were also [having the problem even when using a Mac](https://support.logi.com/hc/en-us/community/posts/360050190474-Logitech-MX-Keys-swapped-and-%C2%BA-keys) (!).

Since no solution was provided I happily opened a ticket with Logitech.

After some mail exchange Logi support made me clear that they were not
able to provide any solution because the keyboard was designed for Mac,
not for Windows or Linux.

Since, as you could see in the above link, the Mac users are also
affected by this problem I honestly think is not a design issue but a
simple bug. That the affected keycodes are decimal 49 and 94 is a hint
that somebody could make a typo somewhere, but of course I may be wrong.

## The solutions

### Linux (X Window System)

After trying to use KDE settings and
[xbindkeys](https://www.nongnu.org/xbindkeys/) without luck I resorted
to the good old
[xmodmap](https://www.x.org/archive/X11R6.8.1/doc/xmodmap.1.html) which
allows remapping any key. The result is the `fix-mx-keys-for-mac.sh`
script, which you can run after X has started to fix those keys.

### Linux (Wayland)

I don't use Wayland yet. If you do and have a fix let me know ;-)

### Windows

Because of the Covid-19 pandemic I have to use Windows for working from
home. The MX keys for Mac works fine in windows, but shows the problem
of swapped keys too. Switching keyboards is somewhat inconvenient, so
after some investigation found a [free Microsoft tool for creating keyboard
layouts](https://www.microsoft.com/en-us/download/details.aspx?id=102134).

MSKLC allows also loading an existing layout and generate a modified
one from it. That new layout, with the scancodes swapped was saved to
the `mskeyses.klc` file.

The tool generates directly an executable for installing the layout, but
I've not included those files since they're probably proprietary. You
can load the klc file and [generate it
yourself](https://www.youtube.com/watch?v=87bt7GBM02M).

Note that the new layout appears in the the language bar just after
installing, and seems available for switching, but it won't work
properly until you restart Windows.

