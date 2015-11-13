---
layout: post
title: Update a symlink
---

To update a symlink in place, without having to delete and recreate:

```
ln -sfn [source file] [target file]
```

What do the flags mean?

```
-s, –symbolic
make symbolic links instead of hard links

-f, –force
remove existing destination files

-n, –no-dereference
treat destination that is a symlink to a directory as if it were a normal file
```

These flags allow for a symlink to a directory to be updated in place.
