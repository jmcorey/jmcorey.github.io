---
layout: post
title: hack to colorize STL code properly
---

```
au BufRead /usr/include/c++/** set filetype=cpp
```

This is one way to make vim do syntax highlighting on the builtin C++ code even
though it lacks any sort of c++ extensions.  Surely there's a more general
problem, but it's not bad as a method of quick hack.
