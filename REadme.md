## Row Sums of A Multiplicative Combinatorial Array of a triangle (equilateral triangle format)

**Author:** Batu J. J. Yagah
email:batujonas.18@gmail.com
The row sum \( S(n) \) counts the total number of configurations for a given total size \( n \), summing over all possible numbers of leaders \( k \):

\[
S(n) = \sum_{k=1}^{n} k \cdot (k+1)^{\,n-k}
\]

| n  | S(n)          |
|----|---------------|
| 1  | 1             |
| 2  | 4             |
| 3  | 13            |
| 4  | 42            |
| 5  | 143           |
| 6  | 522           |
| 7  | 2 047         |
| 8  | 8 596         |
| 9  | 38 485        |
| 10 | 182 904       |
| 11 | 919 145       |
| 12 | 4 866 870     |
| 13 | 27 068 419    |
| 14 | 157 693 006   |
| 15 | 959 873 707   |
| 16 | 6 091 057 008 |
| 17 | 40 213 034 873|
| 18 | 275 699 950 380|
| 19 | 1 959 625 294 309|
| 20 | 14 418 124 498 210|
### Verification
Other sequence by the author https://github.com/yagah1/yagah1Mworks/blob/8dcea0b25cc4edaf176ad06c4ea80b05398bd23f/README.md

```python
def row_sum(n):
    return sum(k * (k + 1) ** (n - k) for k in range(1, n + 1))

for n in range(1, 21):
    print(f"S({n:2d}) = {row_sum(n)}")
