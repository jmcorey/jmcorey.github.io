---
layout: post
title: Vim and STL c++ headers
---

The files in /usr/include/c++ don't have a .cpp extension, so vim by default
does not colorize them, but you can easily fix that.  In your .vimrc:

```
au BufRead /usr/include/c++/** set filetype=cpp
```

This is one way to make vim do syntax highlighting on the STL C++ code even
though it lacks any sort of c++ extensions.  There's probably a more proper
solution for the specific problem...

But this is a nice general purpose quick hack.
