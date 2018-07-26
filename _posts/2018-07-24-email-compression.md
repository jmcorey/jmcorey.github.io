---
layout: post
title: Zstandard compression FTW
---

The `zstd` compression tool seems like a good general purpose choice these days.

There are some exotic compression systems (e.g. phda9, cmix) vying for the
absolute best compression ratio at the [Large Text Compression
Benchmark](http://mattmahoney.net/dc/text.html), most of which are
prohibitively expensive in CPU.  I wanted to check for myself, so I did some
measurements against a bunch of different systems which were come pre-packaged
for linux--no install effort needed.  I included zpaq for comparison, though it
has a clumsy windows-ish interface, and runs very slowly, so I wouldn't
normally use it.  But as you can see, compression has evolved a lot since the
days when .Z was the only item on the NeXT menu.  There is now... too much to
choose from.

Here are some measurements taken against various files, followed by notes
and conclusions.

*No effort was made to enable multi-threaded operation.  Please bear in mind
that the CPU number will of course vary based on the type of machine and the
quality of implementation.  For example, the zpaq numbers probably reflect
the lack of speed optimization of a reference compression implementation.*

### Inbox file

This file is a large email inbox file I had on my system.

I'd probably choose `zstd -9` since I don't care too much about maximizing
compression, just don't want to spend a whole lot of CPU time.

| method | bytes | compress ratio | compress time | decompress time |
|:------   |:---------| ----:| ------:| ------:|
| cat      | 63968176 | 1.00 |   0.00 |   0.00 |
| compress | 38488271 | 1.66 |   2.05 |    .75 |
| lz4      | 31456054 | 2.03 |   0.18 |   0.12 |
| lz4 -16  | 27675433 | 2.31 |  30.96 |   0.12 |
| gzip     | 23130148 | 2.76 |   2.76 |   0.56 |
| gzip -9  | 23046304 | 2.77 |   4.79 |   0.56 |
| bzip2    | 20549684 | 3.11 |   9.95 |   3.68 |
| zstd     | 17508195 | 3.65 |   0.40 |   0.16 |
| zstd -9  | 15266692 | 4.19 |   1.46 |   0.15 |
| zstd -15 | 13813655 | 4.63 |   8.83 |   0.15 |
| brotli   | 12870847 | 4.97 | 153.01 |   0.28 |
| zstd -19 | 11968246 | 5.34 |  13.46 |   0.15 |
| xz       | 11690140 | 5.47 |  17.41 |   1.34 |
| zstd -22 | 11471746 | 5.57 |  29.83 |   0.18 |
| xz -9    | 11375040 | 5.62 |  19.37 |   1.33 |
| zpaq -m5 | 10711110 | 5.97 | 222.00 | 222.00 |

### Bunch of URLs

This file came from tests for Snappy, and has a representative sample of 10000
URLs.  A different kind of pattern than english text.

Brotli did pretty well--not too surprising given context. LZMA (`xz`) shines
here, but I'd still say `zstd` is a sensible choice if fast compression is
needed.

| method | bytes | compress ratio | compress time | decompress time |
|:------   |:---------| ----:| ------:| ------:|
| cat      |   702087 | 1.00 |   0.00 |   0.00 |
| lz4      |   335857 | 2.09 |   0.00 |   0.00 |
| compress |   303931 | 2.31 |   0.02 |   0.01 |
| lz4 -16  |   242513 | 2.89 |   0.16 |   0.00 |
| gzip     |   223875 | 3.13 |   0.03 |   0.01 |
| gzip -9  |   220198 | 3.18 |   0.05 |   0.01 |
| zstd     |   184268 | 3.81 |   0.01 |   0.00 |
| zstd -9  |   169573 | 4.14 |   0.03 |   0.00 |
| zstd -15 |   164986 | 4.25 |   0.09 |   0.00 |
| bzip2    |   164887 | 4.25 |   0.10 |   0.04 |
| zstd -19 |   160722 | 4.36 |   0.21 |   0.00 |
| zstd -22 |   160014 | 4.38 |   0.62 |   0.00 |
| xz -9    |   151216 | 4.64 |   0.33 |   0.01 |
| xz       |   151216 | 4.64 |   0.28 |   0.02 |
| brotli   |   146295 | 4.79 |   2.35 |   0.00 |
| zpaq -m5 |   135187 | 5.19 |   2.71 |   2.70 |

### Machine code: libxul.so

The file is from firefox and contains about a hundred megabytes of code and data.

I think in this case you would want good compression, but not at the cost of
decode time, so `zstd --ultra -22` seems like a good choice.

I tried some experiments with zstd dictionary training on library files, but
significant improvement was elusive.  Probably works better when it's just a
different language.

| method | bytes | compress ratio | compress time | decompress time |
|:------   |:---------| ----:| ------:| ------:|
| cat      | 99803720 | 1.00 |   0.00 |   0.00 |
| compress | 64826447 | 1.53 |   2.84 |   1.34 |
| lz4      | 57853952 | 1.72 |   0.44 |   0.20 |
| lz4 -16  | 47014212 | 2.12 |  40.27 |   0.20 |
| zstd     | 41399907 | 2.41 |   1.16 |   0.38 |
| gzip     | 41295630 | 2.41 |   6.78 |   1.07 |
| gzip -9  | 41086427 | 2.42 |  16.31 |   1.06 |
| zstd -9  | 38142070 | 2.61 |   4.58 |   0.37 |
| bzip2    | 37510498 | 2.66 |  14.44 |   6.13 |
| zstd -15 | 36927448 | 2.70 |  16.66 |   0.37 |
| zstd -19 | 33677490 | 2.96 |  36.30 |   0.42 |
| zstd -22 | 32903553 | 3.03 |  55.28 |   0.47 |
| brotli   | 31461497 | 3.17 | 433.62 |   0.68 |
| xz       | 30565788 | 3.26 |  56.37 |   2.73 |
| xz -9    | 30149092 | 3.31 |  65.01 |   2.81 |
| zpaq -m5 | 25530939 | 3.90 | 274.45 | 276.17 |

### SAO star catalog

This file came from the SAO star catalog, representing the category of scientific data.
The data is clearly not very compressible, although the perf trends are broadly similar.

For scientific data, my gut instinct would be to put more emphasis on
compression ratio and be more lenient on compress time, though it's best to
choose based on access patterns.  I think for this type of data I would be
tempted to use `xz`, or maybe one day `zpaq` if there is a fast version.

`bzip2` did very well. `zstd` is still an acceptable choice, but `gzip` is
relatively defensible, especially since it is so standard. Even so, `zstd -9` is
better than `gzip -9` in every measured aspect.

High compression may require domain-specific approaches, just as with
audiovisual data.

| method | bytes | compress ratio | compress time | decompress time |
|:------   |:---------| ----:| ------:| ------:|
| cat      |  7251944 | 1.00 |   0.00 |   0.00 |
| lz4      |  6790464 | 1.06 |   0.04 |   0.02 |
| compress |  6734319 | 1.07 |   0.25 |   0.12 |
| lz4 -16  |  5670974 | 1.27 |   0.88 |   0.02 |
| zstd     |  5556528 | 1.30 |   0.15 |   0.03 |
| gzip     |  5332822 | 1.35 |   0.68 |   0.09 |
| gzip -9  |  5327037 | 1.36 |   0.80 |   0.09 |
| zstd -9  |  5239710 | 1.38 |   0.61 |   0.03 |
| zstd -15 |  5207071 | 1.39 |   1.50 |   0.03 |
| zstd -19 |  5020396 | 1.44 |   2.52 |   0.03 |
| zstd -22 |  5014611 | 1.44 |   2.87 |   0.03 |
| bzip2    |  4940524 | 1.46 |   1.40 |   0.65 |
| brotli   |  4708232 | 1.54 |  24.84 |   0.09 |
| xz -9    |  4415072 | 1.64 |   3.82 |   0.46 |
| xz       |  4415072 | 1.64 |   3.85 |   0.45 |
| zpaq -m5 |  3899262 | 1.85 |  37.84 |  38.40 |

### OSDB MySql file

This file came from the Open Source Database Benchmark, and represents a binary MySql
database file.  These results may be of special interest to database developers.

I would be tempted to use `bzip2` in this case, though `zstd -15` does OK.
What happened here?  Looks like bzip2 went into berzerker mode or something.
There is some very interesting saga to be told here.  Zstd is alright for fast
compress and decompress; xz is still sensible for compression ratio emphasis.

| method | bytes | compress ratio | compress time | decompress time |
|:------   |:---------| ----:| ------:| ------:|
| cat      | 10085684 | 1.00 |   0.00 |   0.00 |
| lz4      |  5261242 | 1.91 |   0.05 |   0.02 |
| compress |  4386421 | 2.29 |   0.40 |   0.13 |
| lz4 -16  |  3956817 | 2.54 |   1.61 |   0.02 |
| gzip     |  3739573 | 2.69 |   0.55 |   0.11 |
| gzip -9  |  3716337 | 2.71 |   0.70 |   0.10 |
| zstd     |  3515362 | 2.86 |   0.12 |   0.03 |
| zstd -9  |  3381596 | 2.98 |   0.50 |   0.03 |
| zstd -15 |  3141663 | 3.21 |   1.41 |   0.03 |
| zstd -19 |  3077192 | 3.27 |   3.85 |   0.04 |
| zstd -22 |  3068334 | 3.28 |   5.30 |   0.04 |
| xz       |  2850104 | 3.53 |   5.76 |   0.29 |
| xz -9    |  2849908 | 3.53 |   5.85 |   0.29 |
| brotli   |  2846788 | 3.54 |  29.48 |   0.06 |
| bzip2    |  2802792 | 3.59 |   1.40 |   0.59 |
| zpaq -m5 |  2204745 | 4.57 |  40.62 |  40.51 |

### General observations

* compress is a complete joke these days
* zpaq is quite good, but egregiously expensive in both directions
* brotli is also good but expensive... xz -9 is usually better and faster, and sometimes cranking up zstd is competitive
* cranking up lz4 isn't worthwhile--zstd is almost always better and faster
* plain zstd is much smaller than plain lz4, with similar speed
* gzip and bzip2 compress better than lz4, but usually zstd is better and faster
* xz (LZMA) tends to compress better than zstd, but is slower.

### My personal conclusions

* if **compress CPU** is a driving concern: probably just use **zstd** (or nothing)
* if **decompress CPU** is more important: probably use **zstd --ultra -22**
* if **compression ratio** outweighs CPU: probably use **xz -9** (or something exotic)

### Notes on Zstandard

* **.zst** file extension
* developed by Yann Collet at Facebook
* supports custom dictionary training, if desired
* "based on the LZ77 family, with further FSE & huff0 entropy stages"
* "fast modes at > 200 MB/s per core"
* "strong modes nearing LZMA compression ratios"
* "very fast decoder, with speeds > 500 MB/s per core"

