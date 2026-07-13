# Fibonacci Gap Sequence
## Author:Batu J J Yagah
   email: batujonas.18@gmail.com
## Overview

For n ≥ 5, a(n) = (sum of integers strictly between consecutive Fibonacci numbers F(n) and F(n+1)) − F(n), where F(0)=0, F(1)=1.

Sequence: 8, 34, 106, 309, 856, 2321, 6202, 16444, 43382, 114115, 299626, 785841, 2059636, 5395886, 14132578, 37009225, 96907028, 253731169, 664317718, 1739272536, 4553581678, 11921604839, 31211446966, 81713082529, 213928361216, 560072908186

Only 8 = F(6) and 34 = F(9) are Fibonacci numbers.

## Formula

a(n) = ((F(n-1)-1)*(F(n)+F(n+1)))/2 - F(n)

## Examples

n=5: F(5)=5, F(6)=8 → sum between = 13 → a(5)=8
n=6: F(6)=8, F(7)=13 → sum between = 42 → a(6)=34
n=7: F(7)=13, F(8)=21 → sum between = 119 → a(7)=106
n=8: F(8)=21, F(9)=34 → sum between = 330 → a(8)=309

## Conjecture

No term beyond 34 is a Fibonacci number. Verified up to n=100.

## PARI/GP Code

a(n) = my(fnm1=fibonacci(n-1), fn=fibonacci(n), fnp1=fibonacci(n+1)); ((fnm1-1)*(fn+fnp1))/2 - fn

## Mathematica Code

a[n_] := Module[{fnm1=Fibonacci[n-1], fn=Fibonacci[n], fnp1=Fibonacci[n+1]}, ((fnm1-1)*(fn+fnp1))/2 - fn]


