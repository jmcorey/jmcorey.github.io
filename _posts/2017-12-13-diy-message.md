---
layout: post
title: DIY reminder
---

Instead of relying on some desktop-specific notification tool, here is a quick
DIY reminder hack:

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
before waiting, so that if something goes wrong, you'll see it right away.

The *Bahia* was a ship that met with an unfortunate fate.  Look it up for an
amusing story.

This uses the venerable ImageMagick package.  Just think, an open source
utility hacked together almost 30 years ago is still just as useful today.  You
don't see that so much in proprietary software.  Not everything in computers
has to completely be replaced every 5 years.  And on a typical Linux system,
installing is as easy as typing `dnf -y install ImageMagick` or `apt -y install
imagemagick` and there we go, no need to wait around clicking "yes please"
over and over on absurd EULAs etc.  Better yet, you can write a batch file that
does a quiet interaction-free install of your favorite packages, and carry it
with you wherever you go.  Literally if necessary (USB drive).  No reinstall
hells to suffer.

In truth, though, the long-standing name choice `convert` is regrettable.  Not
only does the program do a lot more than convert images from one format to
another, but also, there are other things in the world than just images.
So yeah, stability also has its downsides.

If you need a list of available fonts, you can type:

```
convert -list font
```

If you want a quick way to visually inspect fonts, I find *`fontmatrix`*
more comfortable than, say, *`gnome-font-viewer`*.
