---
layout: post
title: Simple sigwinch watching
---

The POSIX TIOCGWINSZ function gives you the terminal's current window size,
and you can react to changes by registering a SIGWINCH signal handler.

Here's a simple python script to demonstrate.

It's a useful tutorial exercise, but actually I wrote it for a reason,
which is that, although I thank the corporation for letting me have a linux
corporate laptop, I curse them because it's this unholy ubuntu/unity/gnome
crap, and somehow ubuntu has screwed it up so terminals don't show the normal
size information when resized.  But I will not bow down.

```
#!/usr/bin/python3

"""Monitor changes to terminal width and height.

Usage:

  winchwatch
"""

import fcntl
import signal
import struct
import sys
import termios
import time

need_update = True
done = False


def update_screen_size():
    global need_update
    s = struct.pack("HHHH", 0, 0, 0, 0)
    fd_stdout = sys.stdout.fileno()
    dat = fcntl.ioctl(fd_stdout, termios.TIOCGWINSZ, s)
    (height, width) = (struct.unpack("HHHH", dat))[0:2]
    sys.stdout.write("(%d x %d)    \r" % (width, height))
    sys.stdout.flush()
    need_update = False


def handle_sigwinch(signal, frame):
    global need_update
    need_update = True


def handle_deadlysig(signal, frame):
    global done
    done = True


signal.signal(signal.SIGWINCH, handle_sigwinch)
signal.signal(signal.SIGINT, handle_deadlysig)
signal.signal(signal.SIGTERM, handle_deadlysig)

try:
    while not done:
        if need_update:
            update_screen_size()
        time.sleep(0.1)

finally:
    sys.stdout.write("\n")
```
