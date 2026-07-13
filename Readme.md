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

def T(n, k):
    """Return the combinatorial value for row n, column k."""
    return k * (k + 1) ** (n - k)


def print_triangle(max_n=10):
    """Print the triangle in plain text, right-angle format."""
    print("Combinatorial Multiplicative Array (Right-Angle Triangle)")
    print("T(n,k) = k × (k+1)^(n−k)\n")

    # Print header row (column indices)
    print("n\\k", end="")
    for k in range(1, max_n + 1):
        print(f"{k:>7}", end="")
    print()
    print("-" * (7 * max_n + 4))

    # Print each row (right-angle: row n has columns 1 through n)
    for n in range(1, max_n + 1):
        print(f"{n:2} |", end="")
        for k in range(1, n + 1):
            print(f"{T(n, k):>7}", end="")
        print()


if __name__ == "__main__":
    print_triangle(10)
