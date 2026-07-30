# Prime Density Triangle - Equilateral Format (Pyramid)
(based on the researcher's paper on Prime density triangle -A mathematical framework deriving nuclear magic numbers, shell gap and subshell structures)
**Author**: Batu J J Yagah (GES)  
https://doi.org/10.5281/zenodo.21710920
**Email**: batujonas.18@gmail.com  
---

## Overview

The Prime Density Triangle in equilateral (pyramid) format is obtained by mirroring the right-angle triangle about the central term `X^n`. Each row is symmetric and forms a pyramidal structure.

---

## Mathematical Definition

For row `r` (`r >= 0`) with `X = 2`:

- **Row 0**: `0`
- **Row r** (r ≥ 1):
  - First and last term: `r + 1`
  - Center term: `X^(r+1)`
  - Left side: `[(r+1)(r+2)]², [r(r+1)]³, [(r-1)r]⁴, ..., 6^r`
  - Right side: Mirror of left side

### Row Structure

Row 0: 0

Row 1: 2 + X² + 2

Row 2: 3 + 6² + X³ + 6² + 3

Row 3: 4 + 12² + 6³ + X⁴ + 6³ + 12² + 4

Row 4: 5 + 20² + 12³ + 6⁴ + X⁵ + 6⁴ + 12³ + 20² + 5

Row 5: 6 + 30² + 20³ + 12⁴ + 6⁵ + X⁶ + 6⁵ + 12⁴ + 20³ + 30² + 6

Row 6: 7 + 42² + 30³ + 20⁴ + 12⁵ + 6⁶ + X⁷ + 6⁶ + 12⁵ + 20⁴ + 30³ + 42² + 7

Row 7: 8 + 56² + 42³ + 30⁴ + 20⁵ + 12⁶ + 6⁷ + X⁸ + 6⁷ + 12⁶ + 20⁵ + 30⁴ + 42³ + 56² + 8

Row 8: 9 + 72² + 56³ + 42⁴ + 30⁵ + 20⁶ + 12⁷ + 6⁸ + X⁹ + 6⁸ + 12⁷ + 20⁶ + 30⁵ + 42⁴ + 56³ + 72² + 9

```

---

## Evaluated Triangle (with X = 2)

```

Row 0: 0

Row 1: 2 + 4 + 2

Row 2: 3 + 36 + 8 + 36 + 3

Row 3: 4 + 144 + 216 + 16 + 216 + 144 + 4

Row 4: 5 + 400 + 1728 + 1296 + 32 + 1296 + 1728 + 400 + 5

Row 5: 6 + 900 + 8000 + 20736 + 7776 + 64 + 7776 + 20736 + 8000 + 900 + 6

Row 6: 7 + 1764 + 27000 + 160000 + 248832 + 46656 + 128 + 46656 + 248832 + 160000 + 27000 + 1764 + 7

Row 7: 8 + 3136 + 74088 + 810000 + 3200000 + 2985984 + 279936 + 256 + 279936 + 2985984 + 3200000 + 810000 + 74088 + 3136 + 8

Row 8: 9 + 5184 + 175616 + 3111696 + 24300000 + 64000000 + 35831808 + 1679616 + 512 + 1679616 + 35831808 + 64000000 + 24300000 + 3111696 + 175616 + 5184 + 9

```

---

## Row Sums

| Row | Terms | Sum |
|-----|-------|-----|
| 0 | 0 | 0 |
| 1 | 2 + 4 + 2 | 8 |
| 2 | 3 + 36 + 8 + 36 + 3 | 86 |
| 3 | 4 + 144 + 216 + 16 + 216 + 144 + 4 | 744 |
| 4 | 5 + 400 + 1728 + 1296 + 32 + 1296 + 1728 + 400 + 5 | 6,890 |
| 5 | 6 + 900 + 8000 + 20736 + 7776 + 64 + 7776 + 20736 + 8000 + 900 + 6 | 74,900 |
| 6 | 7 + 1764 + 27000 + 160000 + 248832 + 46656 + 128 + 46656 + 248832 + 160000 + 27000 + 1764 + 7 | 968,646 |
| 7 | 8 + 3136 + 74088 + 810000 + 3200000 + 2985984 + 279936 + 256 + 279936 + 2985984 + 3200000 + 810000 + 74088 + 3136 + 8 | 14,705,560 |
| 8 | 9 + 5184 + 175616 + 3111696 + 24300000 + 64000000 + 35831808 + 1679616 + 512 + 1679616 + 35831808 + 64000000 + 24300000 + 3111696 + 175616 + 5184 + 9 | 258,208,870 |

### Row Sums Sequence

```

0, 8, 86, 744, 6890, 74900, 968646, 14705560, 258208870, ...

```

---

## Python Implementation

```python
def prime_density_equilateral(r, x=2):
    """Equilateral Prime Density Triangle (Pyramid) - Batu J J Yagah (GES)"""
    if r == 0:
        return [0]
    
    # Build left side
    left = []
    
    # First term: r + 1
    left.append(r + 1)
    
    # Middle terms: going from [(r+1)(r+2)]^2 down to 6^r
    for k in range(2, r + 1):
        base = (r - k + 2) * (r - k + 3)
        exp = k
        left.append(base ** exp)
    
    # Center term: X^(r+1)
    center = x ** (r + 1)
    
    # Right side is mirror of left (excluding center)
    right = left[::-1]
    
    # Full row: left + [center] + right
    return left + [center] + right

def equilateral_row_sum(r, x=2):
    """Calculate row sum for the equilateral Prime Density Triangle"""
    row = prime_density_equilateral(r, x)
    return sum(row)

# Generate and display the equilateral triangle
print("=" * 80)
print("Prime Density Triangle (Equilateral/Pyramid Format)")
print("Author: Batu J J Yagah (GES)")
print("=" * 80)
print()

for r in range(9):
    row = prime_density_equilateral(r)
    s = equilateral_row_sum(r)
    row_str = ' + '.join(map(str, row))
    print(f"Row {r}: {row_str} | Sum = {s:,}")
```

---

Output from Python Code

```
================================================================================
Prime Density Triangle (Equilateral/Pyramid Format)
Author: Batu J J Yagah (GES)
================================================================================

Row 0: 0 | Sum = 0
Row 1: 2 + 4 + 2 | Sum = 8
Row 2: 3 + 36 + 8 + 36 + 3 | Sum = 86
Row 3: 4 + 144 + 216 + 16 + 216 + 144 + 4 | Sum = 744
Row 4: 5 + 400 + 1728 + 1296 + 32 + 1296 + 1728 + 400 + 5 | Sum = 6,890
Row 5: 6 + 900 + 8000 + 20736 + 7776 + 64 + 7776 + 20736 + 8000 + 900 + 6 | Sum = 74,900
Row 6: 7 + 1764 + 27000 + 160000 + 248832 + 46656 + 128 + 46656 + 248832 + 160000 + 27000 + 1764 + 7 | Sum = 968,646
Row 7: 8 + 3136 + 74088 + 810000 + 3200000 + 2985984 + 279936 + 256 + 279936 + 2985984 + 3200000 + 810000 + 74088 + 3136 + 8 | Sum = 14,705,560
Row 8: 9 + 5184 + 175616 + 3111696 + 24300000 + 64000000 + 35831808 + 1679616 + 512 + 1679616 + 35831808 + 64000000 + 24300000 + 3111696 + 175616 + 5184 + 9 | Sum = 258,208,870
```

---

Visual Representation (Pyramid)

```
Row 0:                      0

Row 1:                   2 + 4 + 2

Row 2:                3 + 36 + 8 + 36 + 3

Row 3:             4 + 144 + 216 + 16 + 216 + 144 + 4

Row 4:         5 + 400 + 1728 + 1296 + 32 + 1296 + 1728 + 400 + 5

Row 5:     6 + 900 + 8000 + 20736 + 7776 + 64 + 7776 + 20736 + 8000 + 900 + 6

Row 6: 7 + 1764 + 27000 + 160000 + 248832 + 46656 + 128 + 46656 + 248832 + 160000 + 27000 + 1764 + 7
```

---

Relationship to Right-Angle Triangle

The equilateral triangle is formed by mirroring the right-angle triangle about the central term X^n.

Right-Angle Triangle (for reference)

```
Row 0: 1
Row 1: 4, 2
Row 2: 8, 36, 3
Row 3: 16, 216, 144, 4
Row 4: 32, 1296, 1728, 400, 5
Row 5: 64, 7776, 20736, 8000, 900, 6
```

Mirror Relationship

· Right-angle triangle row r becomes the left half of equilateral row r-1
· Example: Right-angle Row 3 (16, 216, 144, 4) appears in Equilateral Row 4 as 4, 144, 216, 16

---

Related OEIS Sequences

Sequence Description
A000079 Powers of 2
A000400 Powers of 6
A001021 Powers of 12
A000292 Tetrahedral numbers
A000217 Triangular numbers
A006527 Related to magic numbers
A007290 Harmonic oscillator magic numbers
A005897 Two-spin-orientation magic numbers
A018226 Standard nuclear magic numbers

---

References

1. Mayer, M. G. "On Closed Shells in Nuclei. II." Phys. Rev. 75 (1949): 1969-1970.
2. Haxel, O., Jensen, J. H. D., and Suess, H. E. "On the 'Magic Numbers' in Nuclear Structure." Phys. Rev. 75 (1949): 1766.
3. OEIS Foundation Inc. Sequence A005897, A018226, A007290. https://oeis.org
4. Yagah, B. J. J. "Prime Density Triangle - A Mathematical Framework Deriving Nuclear Magic Numbers and Nuclear Subshell Structure." Zenodo (2026). 10.5281/zenodo.20233053

---

License

This work is shared for academic and research purposes.
see related sequence by the author:https://github.com/yagah1/yagah1Mworks/blob/8d8f224602520570e47855d03561592998e6be69/README.md
