# Find Second Smallest and Second Largest Element in an Array

A Python program that determines the second smallest and second largest distinct elements in an array using a single traversal.

## Overview

Instead of sorting the array, the program maintains two candidates for each side:

* `small` and `second_small` for the two smallest distinct values
* `large` and `second_large` for the two largest distinct values

As each element is examined, the candidates are updated whenever a better value is found. Duplicate values are ignored when determining the second position.

## How It Works

### Finding the Second Smallest

The algorithm begins with both values set to positive infinity.

```python
small = float('inf')
second_small = float('inf')
```

For every element:

1. If it is smaller than `small`, the current `small` becomes `second_small`.
2. Otherwise, if it is smaller than `second_small` and different from `small`, it becomes the new `second_small`.

This logic is implemented directly in the `secondSmallest()` function.

### Finding the Second Largest

The same idea is applied in reverse.

```python
large = float('-inf')
second_large = float('-inf')
```

During the traversal:

1. A value larger than `large` becomes the new largest value.
2. The previous largest value moves into `second_large`.
3. A distinct value between the largest and second-largest candidates updates `second_large`.

The implementation also excludes duplicate copies of the largest value.

## Example

Given:

```python
arr = [1, 3, 4, 7, 7, 11]
```

The distinct values in sorted order would be:

```text
1, 3, 4, 7, 11
```

Therefore:

```text
Second smallest = 3
Second largest  = 7
```

The program produces these results through the two functions called in the main section.

## Complexity

| Metric          | Complexity |
| --------------- | ---------- |
| Time            | O(N)       |
| Auxiliary Space | O(1)       |

Each function scans the array once and uses only a fixed number of variables.

## Edge Case

Both functions return `-1` when the array contains fewer than two elements.
Note that the code does not explicitly handle the case where an array has at least two elements but fewer than two distinct values. In such a case, the sentinel value may be returned.
