"""
Combinatorial Multiplicative Array (Right-Angle Triangle)
Author: Batu J J Yagah

EXTENDED DESCRIPTION:
This right‑angle triangle is defined by T(n,k) = k × (k+1)^(n−k) for 1 ≤ k ≤ n.

Combinatorially: choose a leader (k ways), then assign each of the remaining n−k 
members to one of (k+1) followership levels.

Structurally: it counts rooted trees of height 2 where the root has out‑degree k, 
and its leaves are colored with (k+1) colors.

The array grows multiplicatively and forms a strictly lower‑triangular (right‑angled) shape.
"""

TRIANGLE = """
Combinatorial Multiplicative Array (Right-Angle Triangle)
T(n,k) = k × (k+1)^(n−k)

n\k      1       2       3       4       5       6       7       8       9      10
----------------------------------------------------------------------------------
 1 |     1
 2 |     2       2
 3 |     4       6       3
 4 |     8      18      12       4
 5 |    16      54      48      20       5
 6 |    32     162     192     100      30       6
 7 |    64     486     768     500     180      42       7
 8 |   128    1458    3072    2500    1080     294      56       8
 9 |   256    4374   12288   12500    6480    2058     448      72       9
10 |   512   13122   49152   62500   38880   14406    3584     648      90      10
"""

if __name__ == "__main__":
    print(TRIANGLE)
