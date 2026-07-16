# Prime Density Triangle
(based on the researcher's paper titled: Prime density triangle -A mathematical framework deriving nuclear magic numbers, shell gap and subshell structures)
Author: Batu J J Yagah (GES)
Email: batujonas.18@gmail.com

## Description
Prime Density Triangle, right-angle format.

Row r (r>=0):
T(r,0)=2^(r+1) for r>=1 (T(0,0)=1)
T(r,k)=[k(k+1)]^(r+2-k) for 1<=k<=r
T(r,r+1)=r+1
Evaluated at x=2.

## Rows
Row 0: 1
Row 1: 4, 2
Row 2: 8, 36, 3
Row 3: 16, 216, 144, 4
Row 4: 32, 1296, 1728, 400, 5
Row 5: 64, 7776, 20736, 8000, 900, 6
Row 6: 128, 46656, 248832, 160000, 27000, 1764, 7
Row 7: 256, 279936, 2985984, 3200000, 810000, 74088, 3136, 8

## Properties
Using a four-rule division scheme on the unconverted rows, the integer parts give the two-spin-orientation magic numbers (0,2,6,14,28,50,82,126,184,…). Replacing the repeated end integers by 1,1 yields the harmonic oscillator magic numbers (2,8,20,40,70,112,…). Combining these gives the standard nuclear magic numbers (2,8,20,28,50,82,126,184,…).

## Related Sequences
A000079, A000400, A001021, A000292, A000217, A006527, A007290, A018226

Prime Density Triangle

Row 0: 1
Row 1: 4, 2
Row 2: 8, 36, 3
Row 3: 16, 216, 144, 4
Row 4: 32, 1296, 1728, 400, 5
Row 5: 64, 7776, 20736, 8000, 900, 6
Row 6: 128, 46656, 248832, 160000, 27000, 1764, 7
Row 7: 256, 279936, 2985984, 3200000, 810000, 74088, 3136, 8

def prime_density_right_angle(r, x=2):
    if r == 0:
        return [1]
    row = [x ** (r + 1)]
    for k in range(1, r):
        base = k * (k + 1)
        exp = r + 2 - k
        row.append(base ** exp)
    row.append(r + 1)
    return row

for r in range(10):
    print(f"Row {r}: {', '.join(map(str, prime_density_right_angle(r)))}")
