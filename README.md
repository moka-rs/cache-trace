# Cache Trace

A collection of production cache traces.

This repository contains trace files that can be used to evaluate caching
algorithms.

## Trace Sources

These traces are organized by directory, with each directory containing traces
from a different source.

### ARC Traces

`arc` directory contains some of the traces from the ARC paper:

- [Nimrod Megiddo] and [Dharmendra S. Modha], "ARC: A Self-Tuning, Low Overhead
  Replacement Cache," USENIX Conference on File and Storage Technologies (FAST
  03), San Francisco, CA, pp. 115-130, March 31-April 2, 2003.
  ([PDF][arc-paper])

[Nimrod Megiddo]: http://theory.stanford.edu/~megiddo/bio.html
[Dharmendra S. Modha]: https://researcher.watson.ibm.com/researcher/view_person_subpage.php?id=4700
[arc-paper]: https://www.usenix.org/event/fast03/tech/full_papers/megiddo/megiddo.pdf

See the [README](./arc/README.md) in the `arc` directory for more information
including the conditions of use and redistribution.

## Usage

### Decompressing Trace Files

Trace files may be compressed. See the following table for the command to
decompress.

| File Extension | File Type | Command to Decompress |
|:--|:--|:--|
| `.zstd` | [Zstandard][zstd] |`zstd -d TRACE.zstd` |

#### Installing Zstandard

Here are some command examples to install Zstandard.

On Ubuntu:

```console
$ sudo apt install zstd
```

On macOS using Homebrew:

```console
$ brew install zstd
```

[zstd]: https://facebook.github.io/zstd/

## FAQ

### Why are you using regular `git` instead of `git-lfs` to store traces?

Git Large Storage (LFS) is the proper approach to store binary archives. However
GitHub limits this to 1 GB for free, for all repositories owned by a user. In
addition to that, any fork by any other user consumes _the root repository's
bandwidth_.

This makes LFS unattractive for public repositories as LFS stops working if they
become popular, unless the user pays per-GB prices. It is better then to store
the files directly in git, even if a poor practice.

- [About storage and bandwidth usage | GitHub Docs][gh-storage-usage]

[gh-storage-usage]: https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-storage-and-bandwidth-usage
