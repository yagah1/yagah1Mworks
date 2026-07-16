# Prime Density Triangle (Right-Angle Format)
(based on the researcher's paper on prime density triangle -A mathematical framework deriving nuclear magic numbers, shell gap and subshell structures)
Author: Batu J J Yagah (GES)
Email: batujonas.18@gmail.com

## Row Sums
Row sums of the prime density triangle (right-angle format).
Formula: a(n) = 2^(n+1) + (n+1) + sum from k=2 to n of [k(k+1)]^(n+2-k)
1, 6, 47, 380, 3461, 37482, 484387, 7353408, 129104441, 2589967502, 58757627063, 1488022538280, 41671818286961, 1281092143369042, 42878588281341243

def prime_density_right_angle(r, x=2):
    """Right-angle Prime Density Triangle - Batu J J Yagah (GES)"""
    if r == 0:
        return [1]
    row = [x ** (r + 1)]
    for k in range(1, r + 1):
        base = (k + 1) * (k + 2)
        exp = r + 1 - k
        row.append(base ** exp)
    row.append(r + 1)
    return row

def row_sum(r, x=2):
    """Calculate row sum for the right-angle Prime Density Triangle"""
    row = prime_density_right_angle(r, x)
    return sum(row)

# Generate and display the triangle
print("=" * 80)
print("Prime Density Triangle (Right-Angle Format)")
print("Author: Batu J J Yagah (GES)")
print("=" * 80)
print()

for r in range(12):
    row = prime_density_right_angle(r)
    s = row_sum(r)
    row_str = ', '.join(map(str, row))
    print(f"Row {r:2d}: {row_str} | Sum = {s:,}")

print()
print("=" * 80)
print("Row Sums Sequence:")
print("=" * 80)
sums = [row_sum(r) for r in range(12)]
print(', '.join(map(str, sums)))

Related sequence on the right angle triangle format itself https://github.com/yagah1/yagah1Mworks/blob/965d24a06d8ec879e643daae378696dac3a83f3f/Prime%20density%20Readme.md
