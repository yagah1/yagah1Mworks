# QCR — Quantum Crash Rhythm
Author:Batu J J Yagah (GES)
department of science and mathematics, Diabene SHTS 
email: batujonas.18@gmail.com
**A digit‑sum sawtooth sequence born from a quantum computing constant.**

---

## The Sequence

Define  
\[
QCR(n) = \text{sum of decimal digits}\bigl(\lfloor c \cdot \sqrt{n} \rfloor\bigr)
\]
where \( c = \frac{9}{2\ln 2} \approx 6.4921 \) is the **BBHT constant** — the optimal expected number of quantum oracle queries needed to search an unstructured database of size \(n\) when the number of solutions is unknown (Boyer, Brassard, Høyer, Tapp, 1998).

---

## Behaviour

- **Slow climb** — as \(n\) grows, \(\sqrt{n}\) grows, so \(\lfloor c\sqrt{n} \rfloor\) increases. The digit‑sum gently rises.
- **Sudden crash** — whenever \(\lfloor c\sqrt{n} \rfloor\) crosses a multiple of 10 (e.g. 19→20, 29→30), the digit‑sum collapses.  
  This creates a **sawtooth** pattern: steady ascent, abrupt drop, repeat.

The crashes are **not** a new quantum phenomenon — they are an artefact of base‑10 digit‑sum — but they give the sequence a mesmerising, breathing rhythm perfect for creative applications.

---

## First 30 terms

| n | floor(c√n) | QCR(n) |
|---|------------|--------|
| 1 | 6          | 6      |
| 2 | 9          | 9      |
| 3 | 11         | 2      | ← crash
| 4 | 12         | 3      |
| 5 | 14         | 5      |
| 6 | 15         | 6      |
| 7 | 17         | 8      |
| 8 | 18         | 9      |
| 9 | 19         | 10     |
|10 | 20         | 2      | ← crash
|11 | 21         | 3      |
|12 | 22         | 4      |
|13 | 23         | 5      |
|14 | 24         | 6      |
|15 | 25         | 7      |
|16 | 25         | 7      |
|17 | 26         | 8      |
|18 | 27         | 9      |
|19 | 28         | 10     |
|20 | 29         | 11     |
|21 | 29         | 11     |
|22 | 30         | 3      | ← crash
|23 | 31         | 4      |
|24 | 31         | 4      |
|25 | 32         | 5      |
|26 | 33         | 6      |
|27 | 33         | 6      |
|28 | 34         | 7      |
|29 | 34         | 7      |
|30 | 35         | 8      |

---

## Applications (the “why”)

- 🎵 **Procedural music** — map QCR(n) to a scale; the crashes create natural phrase endings.
- 🎮 **Game level design** — enemy wave difficulty / terrain height that “breathes”.
- 🎨 **Generative art** — use as radius, brightness, or colour index for a sawtooth aesthetic.
- 🧪 **Teaching tool** — demonstrates floor, sqrt, digit‑sum, and sensitivity to carries in a single formula.

---

## Credits

- Constant \(c\) from *Boyer, Brassard, Høyer, Tapp, “Tight bounds on quantum searching”*, 1998.
- Sequence concept & name *QCR (Quantum Crash Rhythm)* by [your name/handle].

---

## License

MIT — use it, remix it, play with it.

import math

C = 9 / (2 * math.log(2))

def qcr(n, base=10):
    if n < 1:
        raise ValueError("n must be >= 1")
    x = math.floor(C * math.sqrt(n))
    s = 0
    while x > 0:
        s += x % base
        x //= base
    return s if s > 0 else 1

if __name__ == "__main__":
    print([qcr(i) for i in range(1, 31)])
    Other sequences by the author https://github.com/yagah1/yagah1Mworks/blob/8d8f224602520570e47855d03561592998e6be69/README.md
