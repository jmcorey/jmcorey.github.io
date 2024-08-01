---
layout: post
title: Use rsync to discover missing files
---

```
rsync -rnv --size-only dir/ remote:dir/
```

This will tell you what files are present locally but missing remotely, without
tranferring anything.  It seems more convenient than making two sorted find
output files and diffing those files.

Since it is in dry-run mode, you can use `--delete` to also show files present
remotely and missing locally, but perhaps you find it uncomfortable typing that
word (I certainly do), in which just you may prefer to just re-run with
direction reversed to find files present only on the remote end.
