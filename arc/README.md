## ARC Trace Datasets

These traces are released under the condition that the "ARC" paper must be
cited:

- [Nimrod Megiddo] and [Dharmendra S. Modha], "ARC: A Self-Tuning, Low Overhead
  Replacement Cache," USENIX Conference on File and Storage Technologies (FAST
  03), San Francisco, CA, pp. 115-130, March 31-April 2, 2003.
  ([PDF][arc-paper])

[Nimrod Megiddo]: http://theory.stanford.edu/~megiddo/bio.html
[Dharmendra S. Modha]: https://researcher.watson.ibm.com/researcher/view_person_subpage.php?id=4700
[arc-paper]: https://www.usenix.org/event/fast03/tech/full_papers/megiddo/megiddo.pdf

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

| Value | Description |
|--:|:--|
| 110765 | Starting block
| 64 | 64 blocks each of 512 bytes so this represents 64 requests (each of a 512 byte page) from 110765 to 110828 |
| 0	| ignore |
| 0 | Request number (goes from 0 to n-1) |
