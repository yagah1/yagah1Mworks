"""
Combinatorial Multiplicative Array (Right-Angle Triangle Format)
Author: Batu J J Yagah

This triangle counts configurations in a leaders-followers model:
T(n, k) = k * (k + 1)^(n - k)

Where:
- n = total members
- k = chosen leader (1 ≤ k ≤ n)
- (k+1) = number of followership levels assigned to the remaining n-k members.

Equivalent interpretation: Number of rooted trees of height 2 with root degree k
and leaves colored with k+1 colors.
"""

def T(n: int, k: int) -> int:
    """Return the combinatorial multiplicative value for row n, column k."""
    return k * (k + 1) ** (n - k)


def generate_triangle(max_n: int = 10):
    """
    Print the Combinatorial Multiplicative Array in right-angle triangle format.
    Rows are indexed by n, columns by k (left-aligned to the right angle).
    """
    print(f"Combinatorial Multiplicative Array (Right-Angle Format) - n=1 to {max_n}\n")
    
    # Print header
    print("n\\k", end="")
    for k in range(1, max_n + 1):
        print(f"{k:>10}", end="")
    print("\n" + "-" * (10 * max_n + 4))

    # Print rows (right-angle triangle: row n has columns 1 through n)
    for n in range(1, max_n + 1):
        print(f"{n:2} |", end="")
        for k in range(1, n + 1):
            print(f"{T(n, k):>10,}", end="")
        print()


def get_row(n: int) -> list:
    """Return a single row (n) as a list of integers."""
    return [T(n, k) for k in range(1, n + 1)]


def get_all_rows(max_n: int = 12) -> dict:
    """Return all rows up to max_n as a dictionary {n: [values]}."""
    return {n: get_row(n) for n in range(1, max_n + 1)}


# ========== EXECUTION ==========
if __name__ == "__main__":
    # Generate the corrected triangle up to n=10
    generate_triangle(10)

    print("\n" + "=" * 60)
    print("Example: Row 10 as a Python list (for verification)")
    print(get_row(10))
    
    print("\n" + "=" * 60)
    print("All rows up to 12 (raw dictionary format):")
    print(get_all_rows(12))
