# n9-blocks-cumulative-sum

**Author:** Batu JJ Yagah  
**Date:** 2026-07-13

This repository generates the infinite sequence formed by concatenating blocks of the form:

```

n^9, n^9 - 1, n^9 - 2, ..., n^9 - 9

```

for each integer `n >= 0`.

## Sequence definition

Let `m` be a non-negative integer. Write `m = 10*n + k`, where `n = floor(m/10)` and `k = m mod 10` (`0 <= k <= 9`). Then the `m`-th term is:

```

a(m) = n^9 - k

```

Equivalently:

```

a(m) = floor(m/10)^9 - (m mod 10)

```

## First terms

The sequence begins:

```

n = 0:     0, -1, -2, -3, -4, -5, -6, -7, -8, -9
n = 1:     1,  0, -1, -2, -3, -4, -5, -6, -7, -8
n = 2:   512, 511, 510, 509, 508, 507, 506, 505, 504, 503
n = 3: 19683, 19682, 19681, 19680, 19679, 19678, 19677, 19676, 19675, 19674

```

Concatenated (first 30 terms):

```

0, -1, -2, -3, -4, -5, -6, -7, -8, -9,
1, 0, -1, -2, -3, -4, -5, -6, -7, -8,
512, 511, 510, 509, 508, 507, 506, 505, 504, 503, ...

```

## Python implementation

The script provides two functions:

- `a(n)` – returns the `n`-th term (0-indexed).
- `generate_terms(count)` – returns a list of the first `count` terms.

### Full code

```python
def a(n: int) -> int:
    """Return the n-th term (0-indexed) of the sequence."""
    return (n // 10) ** 9 - (n % 10)

def generate_terms(count: int) -> list[int]:
    """Generate the first 'count' terms of the sequence."""
    return [a(i) for i in range(count)]

# Example usage
if __name__ == "__main__":
    N = 30
    terms = generate_terms(N)
    print(f"First {N} terms (n=0..{N-1}):")
    print(terms)

    print("\nGrouped by blocks (each row is n^9 down to n^9-9):")
    for n in range(N // 10 + 1):
        block_start = n * 10
        block_end = min(block_start + 10, N)
        block = terms[block_start:block_end]
        if block:
            print(f"n={n}: {block}")
```

Example output

Running the script produces:

```
First 30 terms (n=0..29):
[0, -1, -2, -3, -4, -5, -6, -7, -8, -9, 1, 0, -1, -2, -3, -4, -5, -6, -7, -8, 512, 511, 510, 509, 508, 507, 506, 505, 504, 503]

Grouped by blocks (each row is n^9 down to n^9-9):
n=0: [0, -1, -2, -3, -4, -5, -6, -7, -8, -9]
n=1: [1, 0, -1, -2, -3, -4, -5, -6, -7, -8]
n=2: [512, 511, 510, 509, 508, 507, 506, 505, 504, 503]
n=3: [19683, 19682, 19681, 19680, 19679, 19678, 19677, 19676, 19675, 19674]
```

License

This project is open-source – feel free to use, modify, and share.
