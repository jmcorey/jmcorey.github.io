---
layout: post
title: Vim hack: STL c++ headers
---

The files in /usr/include/c++ don't have a .cpp extension, but you can easily
fix that.  For instance, in your .vimrc:

```
au BufRead /usr/include/c++/** set filetype=cpp
```

This is one way to make vim do syntax highlighting on the builtin C++ code even
though it lacks any sort of c++ extensions.  There's probably a more proper
solution for the specific problem...

But it's a nice general purpose quick hack.
