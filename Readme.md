# A combinatorial Multiplicative Array of a triangle(right angle format)

**Author:** Batu J J Yagah
email: batujonas.18@gmail.com
This triangular array counts configurations in a **leaders-followers** model.

## Description
**T(n,k)** = number of ways to:
- Choose a leader (k choices), then
- Assign each of the remaining **n-k** members to one of **k+1** followership levels.

For **1 ≤ k ≤ n**.

### Formula
\[ T(n,k) = k \times (k+1)^{n-k} \]

Equivalently: number of rooted trees of height 2 with root degree k and leaves colored with k+1 colors.

## The Triangle (up to n=10)

| n \ k | 1     | 2     | 3     | 4     | 5     | 6     | 7    | 8    | 9   | 10  |
|-------|-------|-------|-------|-------|-------|-------|------|------|-----|-----|
| 1     | 1     |       |       |       |       |       |      |      |     |     |
| 2     | 2     | 2     |       |       |       |       |      |      |     |     |
| 3     | 4     | 6     | 3     |       |       |       |      |      |     |     |
| 4     | 8     | 18    | 12    | 4     |       |       |      |      |     |     |
| 5     | 16    | 54    | 48    | 20    | 5     |       |      |      |     |     |
| 6     | 32    | 162   | 192   | 100   | 30    | 6     |      |      |     |     |
| 7     | 64    | 486   | 768   | 500   | 180   | 42    | 7    |      |     |     |
| 8     | 128   | 1458  | 3072  | 2500  | 1080  | 294   | 56   | 8    |     |     |
| 9     | 256   | 4374  | 12288 | 12500 | 6480  | 2058  | 448  | 72   | 9   |     |
| 10    | 512   | 13122 | 49152 | 62500 | 38880 | 14406 | 3584 | 648  | 90  | 10  |

## Python Code

```python
def T(n, k):
    return k * (k + 1) ** (n - k)

for n in range(1, 13):
    row = [T(n, k) for k in range(1, n+1)]
    print(f"Row {n}: {row}")
Other sequence by the author https://github.com/yagah1/yagah1Mworks/blob/c642ab676f65ecb533f4b26332a84808c715ed40/Fibonacci-gap-sequence.md
