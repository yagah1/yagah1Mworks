# n9-blocks-cumulative-sum

This repository generates the infinite sequence formed by concatenating blocks of the form:

Sequence of blocks: n^9, n^9-1, ..., n^9-9  for n >= 0.

Definition:
    a(10*n + k) = n^9 - k   for n >= 0,  k = 0..9

First terms (n=0..2):
    0, -1, -2, -3, -4, -5, -6, -7, -8, -9,
    1, 0, -1, -2, -3, -4, -5, -6, -7, -8,
    512, 511, 510, 509, 508, 507, 506, 505, 504, 503, ...

Author: Batu JJ Yagah
Date: 2026-07-12
"""

def a(n: int) -> int:
    """Return the n-th term (0-indexed) of the sequence."""
    return (n // 10) ** 9 - (n % 10)

def generate_terms(count: int) -> list[int]:
    """Generate the first 'count' terms of the sequence."""
    return [a(i) for i in range(count)]

# ----------------------------------------------------------------------
# Example usage
if __name__ == "__main__":
    # Print the first 30 terms (n=0..29)
    N = 30
    terms = generate_terms(N)
    print(f"First {N} terms (n=0..{N-1}):")
    print(terms)

    # Print them grouped by blocks of 10 for clarity
    print("\nGrouped by blocks (each row is n^9 down to n^9-9):")
    for n in range(N // 10 + 1):
        block_start = n * 10
        block_end = min(block_start + 10, N)
        block = terms[block_start:block_end]
        if block:
            print(f"n={n}: {block}")
