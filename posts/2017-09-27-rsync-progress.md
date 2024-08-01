---
layout: post
title: Fix rsync progress
---

Rsync's progress meter is broken by default, but it's easy to fix.

The scene: you're using rsync to copy a bunch of small files via rsync, and you
opt for a progress meter.  You'd probably check the man page and use the -P
option, resulting in something like this:

```
rsync -a -P my_folder/ remote_folder/
```

But hold on... The progress meter flickers between 0% and 100%, apparently
documenting the status of each individual file, rather than the overall
progress, which is presumably what you wanted.

So apparently, if you want the overall progress, i.e. if you want something
sane, don't ask for the default progress meter.  Ask for the other one:

```
rsync -a --info=progress2 my_folder/ remote_folder/
```
