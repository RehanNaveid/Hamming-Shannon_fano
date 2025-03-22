# Exp:8 Huffman and Shannon-Fano

## **Aim**
To implement a program that computes the **average codeword length, entropy, efficiency, redundancy, and variance** for a given set of probabilities and code lengths using Huffman coding.

## **Tools Required**
- Python 3.x
- NumPy (optional for advanced computations)
- Math library (for logarithmic calculations)

## **Program**
```python
import numpy as np
import math

L  = 0
hs = 0
p = []
lk = []

n = int(input("Enter the number of Samples : "))

for i in range(n):
    pr = float(input(f"Enter the probability of sample values {i + 1}: "))
    p.append(pr)
for j in range(n):
    l = float(input(f"Enter the length of the sample values {j + 1}: "))
    lk.append(l)

# Avg length of the codeword
for k in range(n):
    Avg1 = p[k] * lk[k]
    L = L + Avg1

# Entropy
for k in range(n):
    e = p[k] * math.log(1 / p[k], 2)
    hs = hs + e
hs = round(hs, 3)

# Efficiency
eff = hs / L
eff = round(eff, 3)

# Redundancy
red = round(1 - eff, 3)

# Variance
var = 0
for k in range(n):
    var1 = p[k] * (lk[k] - L) ** 2
    var = var + var1
var = round(var, 3)

print(f"Average Codeword Length is : {round(L, 3)}")
print(f"Entropy is : {hs}")
print(f"Efficiency is : {eff}")
print(f"Redundancy is : {red}")
print(f"Variance is : {var}")
```

## **Encoding Table**
| Symbol | Probability | Huffman Code | Code Length |
|--------|------------|-------------|-------------|
| 3      | 0.25       | 00          | 2           |
| 7      | 0.25       | 01          | 2           |
| 1      | 0.125      | 100         | 3           |
| 5      | 0.125      | 101         | 3           |
| 6      | 0.125      | 110         | 3           |
| 2      | 0.0625     | 1110        | 4           |
| 4      | 0.0625     | 1111        | 4           |

## **Input & Execution**
```
Enter the number of Samples : 7
Enter the probability of sample values 1: 0.25
Enter the probability of sample values 2: 0.25
Enter the probability of sample values 3: 0.125
Enter the probability of sample values 4: 0.125
Enter the probability of sample values 5: 0.125
Enter the probability of sample values 6: 0.0625
Enter the probability of sample values 7: 0.0625
Enter the length of the sample values 1: 2
Enter the length of the sample values 2: 2
Enter the length of the sample values 3: 3
Enter the length of the sample values 4: 3
Enter the length of the sample values 5: 3
Enter the length of the sample values 6: 4
Enter the length of the sample values 7: 4
```

## **Output**
```
Average Codeword Length is : 2.625
Entropy is : 2.625
Efficiency is : 1.0
Redundancy is : 0.0
Variance is : 0.484
```

## **Result**
- The **entropy (H)** represents the theoretical minimum average code length.
- The **average code length (L)** matches the entropy, indicating **optimal encoding**.
- The **efficiency** of 100% confirms that Huffman coding has minimized redundancy.
- The **variance** helps measure fluctuations in codeword lengths.


