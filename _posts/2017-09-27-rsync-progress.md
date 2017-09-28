---
layout: post
title: rsync progress meter silliness
---

The scene: you're using rsync to copy a bunch of small files via rsync, and you
want a progress meter.  You'd probably check the man page and type something
like:

```
rsync -a -P my_folder/ remote_folder/
```

But what's this? The progress meter flickers between 0% and 100%, apparently
documenting the status of each individual file, rather than the overall
progress, which is presumably what you wanted.  So apparently, if you want
sane, don't ask for the default progress meter.  Ask for the other one:

```
rsync -a --info=progress2 my_folder/ remote_folder/
```
