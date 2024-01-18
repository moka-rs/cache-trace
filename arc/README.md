# ARC Trace Datasets

These traces are released under the condition that the "ARC" paper must be
cited:

- [Nimrod Megiddo] and [Dharmendra S. Modha], "ARC: A Self-Tuning, Low Overhead
  Replacement Cache," USENIX Conference on File and Storage Technologies (FAST
  03), San Francisco, CA, pp. 115-130, March 31-April 2, 2003.
  ([PDF][arc-paper])

[Nimrod Megiddo]: http://theory.stanford.edu/~megiddo/bio.html
[Dharmendra S. Modha]: https://researcher.watson.ibm.com/researcher/view_person_subpage.php?id=4700
[arc-paper]: https://www.usenix.org/event/fast03/tech/full_papers/megiddo/megiddo.pdf

## Contents of the Trace Files

A quote from the paper:

> ### A. Traces
>
> Table III summarizes various traces that we used in this paper. These traces
> capture disk accesses by databases, web servers, NT workstations, and a
> synthetic benchmark for storage controllers. All traces have been filtered by
> upstream caches, and, hence, are representative of workloads seen by storage
> controllers, disks, or RAID controllers.
>
> | Trace Name | Number of Requests | Unique Pages |
> |:--|--:|--:|
> | OLTP      |    914145 |   186880 |
> | &mdash;   |   &mdash; |  &mdash; |
> | P1        |  32055473 |  2311485 |
> | P2        |  12729495 |   913347 |
> | P3        |   3912296 |   762543 |
> | P4        |  19776090 |  5146832 |
> | P5        |  22937097 |  3403835 |
> | P6        |  12672123 |   773770 |
> | P7        |  14521148 |  1619941 |
> | P8        |  42243785 |   977545 |
> | P9        |  10533489 |  1369543 |
> | P10       |  33400528 |  5679543 |
> | P11       | 141528425 |  4579339 |
> | P12       |  13208930 |  3153310 |
> | P13       |  15629738 |  2497353 |
> | P14       | 114990968 | 13814927 |
> | ConCat    | 490139585 | 47003313 |
> | Merge(P)  | 490139585 | 47003313 |
> | &mdash;   |   &mdash; |  &mdash; |
> | DS1       |  43704979 | 10516352 |
> | &mdash;   |   &mdash; |  &mdash; |
> | SPC1 like |  41351279 |  6050363 |
> | &mdash;   |   &mdash; |  &mdash; |
> | S1        |   3995316 |  1309698 |
> | S2        |  17253074 |  1693344 |
> | S3        |  16407702 |  1689882 |
> | Merge (S) |  37656092 |  4692924 |
>
>> TABLE III. A summary of various traces used in this paper. Number of unique
>> pages in a trace is termed its "footprint".
>
> The trace OLTP has been used in [18], [20], [23]. It contains references to a
> CODASYL database for a one-hour period. The traces P1&mdash;P14 were collected
> from workstations running Windows NT by using Vtrace which captures disk
> operations through the use of device filters. The traces were gathered over
> several months, see [29]. The page size for these traces was bytes. The trace
> ConCat was obtained by concatenating the traces P1&mdash;P14. Similarly, the
> trace Merge(P) was obtained by merging the traces P1&mdash;P14 using time
> stamps on each of the requests. The idea was to synthesize a trace that may
> resemble a workload seen by a small storage controller. The trace DS1 was
> taken off a database server running at a commercial site running an ERP
> application on top of a commercial database. The trace is seven days long, see
> [30]. We captured a trace of the SPC1 like synthetic benchmark that contains
> long sequential scans in addition to random accesses. For precise description
> of the mathematical algorithms used to generate the benchmark, see [31], [32],
> [33]. The page size for this trace was KBytes. Finally, we consider three
> traces S1, S2, and S3 that were disk read accesses initiated by a large
> commercial search engine in response to various web search requests. The trace
> S1 was captured over a period of an hour, S2 was captured over roughly four
> hours, and S3 was captured over roughly six hours. The page size for these
> traces was KBytes. The trace Merge(S) was obtained by merging the traces
> S1&mdash;S3 using time stamps on each of the requests.
>
> For all traces, we only considered the read requests.
>
> - [18] E. J. O’Neil, P. E. O'Neil, and G. Weikum, "The LRU-K page replacement
>        algorithm for database disk buffering," in Proc. ACM SIGMOD Conf., pp.
>        297&mdash;306, 1993.
> - [20] T. Johnson and D. Shasha, "2Q: A low overhead high performance buffer
>        management replacement algorithm," in Proc. VLDB Conf., pp.
>        297&mdash;306, 1994.
> - [23] D. Lee, J. Choi, J.-H. Kim, S. H. Noh, S. L. Min, Y. Cho, and C. S.
>        Kim, "LRFU: A spectrum of policies that subsumes the least recently
>        used and least frequently used policies," IEEE Trans. Computers, vol.
>        50, no. 12, pp. 1352&mdash;1360, 2001.
> - [29] W. W. Hsu, A. J. Smith, and H. C. Young, "The automatic improvement of
>        locality in storage systems." Tech. Rep., Computer Science Division,
>        Univ. California, Berkeley, Nov. 2001.
> - [30] W. W. Hsu, A. J. Smith, and H. C. Young, "Characteristics of I/O traffic
>        in personal computer and server workloads." Tech. Rep., Computer Science
>        Division, Univ. California, Berkeley, July 2001.
> - [31] B. McNutt and S. A. Johnson, "A standard test of I/O cache," in Proc.
>        the Computer Measurements Group’s 2001 International Conference, 2001.
> - [32] S. A. Johnson, B. McNutt, and R. Reich, "The making of a standard
>        benchmark for open system storage," J. Comput. Resource Management, no.
>        101, pp. 26&mdash;32, Winter 2001.
> - [33] B. McNutt, "The Fractal Structure of Data Reference: Applications to
>        the Memory Hierarchy." Boston, MA: Kluwer Academic Publishers, 2000.

## Decompressing Trace Files

These trace files are compressed using [Zstandard][zstd]. If you need to
decompress them, Run the following commands:

```console
$ cd cache-trace/arc
$ zstd -d *.lis.zst
$ cat spc1likeread.lis.zst.* | zstd -d - > spc1likeread.lis
```

You may need to install `zstd` first. See [this chapter][readme-decompress]
for the command.

[zstd]: https://facebook.github.io/zstd/
[readme-decompress]: ../README.md#decompressing-trace-files

## File Format

Every line in every file has four fields.

| Field | Description |
|:--|:--|
| First field  | `starting_block`                             |
| Second field | `number_of_blocks` (each block is 512 bytes) |
| Third field  | ignore                                       |
| Fourth field | `request_number` (starts at 0)               |

### Example

First line in `P6.lis` is `110765 64 0 0`

| Value  | Description |
|-------:|:------------|
| 110765 | Starting block |
| 64     | 64 blocks each of 512 bytes so this represents 64 requests (each of a 512 byte page) from 110765 to 110828 |
| 0	     | ignore |
| 0      | Request number (goes from 0 to n-1) |
