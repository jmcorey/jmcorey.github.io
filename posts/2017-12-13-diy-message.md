---
layout: post
title: DIY reminder
---

Instead of relying on some desktop-specific notification tool, here is a quick
DIY hack for reminders:

```
convert -background black -fill white -font LMRomanCaps10-Oblique -pointsize 90 \
  label:'Remember the Bahia' /tmp/reminder$$.png \
  && sleep 900 \
  && display /tmp/reminder$$.png \
  && rm /tmp/reminder$$.png
```

Sure, it may seem like overkill to render an image, sleep, and then display it,
but you get a lot of flexibility with this approach, and no dependence on a
particular desktop environment's notification system.  The image is rendered
before waiting, so that if it fails, you'll see it immediately.

The *Bahia* was a ship that met with an unfortunate fate.  Look it up for an
amusing story.

This uses the venerable ImageMagick package.  Just think, an open source
utility hacked together almost 30 years ago is still just as useful today.  You
don't see that often, especially not with proprietary software.  But not everything in computers
has to completely be replaced every 5 years.  And on a typical Linux system,
installing is as easy as typing `dnf -y install ImageMagick` or `apt -y install
imagemagick` and there we go, no need to wait around clicking "yes please"
over and over for absurd EULAs etc.  Or, better yet, you can write a batch file that
does a quiet interaction-free install of your favorite packages, and carry it
with you wherever you go.  That's the joy of a package management system built
by and for literate people.  You can rebuild a system from the ground up with
less effort than it takes someone to copy a file between two windows systems.

To be honest, though, the long-standing choice of names (`convert`) is regrettable.  Not
only does the program do a lot more than convert images from one format to
another, but also, there are other things in the world than just images.
So yeah, stability mixed with amateur contributions also has its downsides.

If you need a list of available fonts, you can type:

```
convert -list font
```

If you want a quick way to visually inspect fonts, I find *`fontmatrix`*
more comfortable than, say, the standard *`gnome-font-viewer`*.
