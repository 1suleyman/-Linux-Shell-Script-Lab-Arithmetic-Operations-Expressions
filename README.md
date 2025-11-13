# 🧠 Linux Shell Script Lab – Arithmetic Operations & Expressions

In this lab, I practiced **performing mathematical operations in Bash**, learning how to use arithmetic expansion, command-line arguments, and expressions like `expr` and `bc`.
I also debugged and created scripts for **sum, difference, multiplication, division, and averages**, applying both integer and floating-point calculations.

---

## 📋 Lab Overview

**Goal:**

* Learn how to perform **basic arithmetic in Bash** (`+`, `-`, `*`, `/`)
* Replace static numbers with **command-line parameters**
* Understand how to handle both **integer** and **decimal** operations
* Debug and fix real-world calculation scripts

**Learning Outcomes:**

* Use `$(())` for integer arithmetic
* Use `bc -l` for floating-point division
* Handle mathematical logic through command-line arguments
* Apply good naming practices and debugging techniques for Bash math

---

## 🛠 Step-by-Step Journey

### Step 1 — Update `calculation.sh` to Perform Arithmetic

Script path: `/home/bob/calculation.sh`

**Original:**

```bash
A=20
B=10
echo "Sum is"
echo "Difference is"
echo "Product is"
echo "Quotient is"
```

**Fixed:**

```bash
A=20
B=10

echo "Sum is $((A + B))"
echo "Difference is $((A - B))"
echo "Product is $((A * B))"
echo "Quotient is $((A / B))"
```

✅ Outputs:

```
Sum is 30
Difference is 10
Product is 200
Quotient is 2
```

---

### Step 2 — Replace Static Values with Command-Line Arguments

Modified `/home/bob/calculation.sh` to accept dynamic input:

**Fixed:**

```bash
A=$1
B=$2

echo "Sum is $((A + B))"
echo "Difference is $((A - B))"
echo "Product is $((A * B))"
echo "Quotient is $((A / B))"
```

✅ Test:

```bash
bash calculation.sh 10 5
```

Output:

```
Sum is 15
Difference is 5
Product is 50
Quotient is 2
```

---

### Step 3 — Create `calculate-price.sh`

Script path: `/home/bob/calculate-price.sh`

**Goal:** Multiply two numbers (price × quantity) and print the result with formatted text.

**Script:**

```bash
#!/bin/bash
price=$(($1 * $2))
echo "The total price of items is $price dollars."
```

Make it executable:

```bash
chmod +x /home/bob/calculate-price.sh
```

✅ Test:

```bash
bash calculate-price.sh 200 5
```

Output:

```
The total price of items is 1000 dollars.
```

---

### Step 4 — Fix `calculate-total-apples.sh`

Script path: `/home/bob/calculate-total-apples.sh`

**Original (broken):**

```bash
baskets=4
apples_per_basket=5
total_apples=`expr $baskets * $apples_per_basket`
echo "Total apples = $total_apples"
```

**Issue:** The `*` operator in `expr` must be **escaped** using `\*`.

**Fixed:**

```bash
baskets=4
apples_per_basket=5
total_apples=`expr $baskets \* $apples_per_basket`
echo "Total apples = $total_apples"
```

✅ Output:

```
Total apples = 20
```

---

### Step 5 — Create `calculate-average.sh`

Script path: `/home/bob/calculate-average.sh`

**Goal:** Accept three numbers, find their average, and retain decimals (no rounding).

**Script:**

```bash
#!/bin/bash

num1=$1
num2=$2
num3=$3

sum=$((num1 + num2 + num3))
average=$(echo "$sum / 3" | bc -l)

echo $average
```

Make it executable:

```bash
chmod +x /home/bob/calculate-average.sh
```

✅ Test:

```bash
bash calculate-average.sh 1 2 1
```

Output:

```
1.333333333
```

---

## 🧠 Key Concepts Reinforced

| Concept                  | Description                                    |
| ------------------------ | ---------------------------------------------- |
| **Arithmetic Expansion** | Use `$((expression))` for integer math         |
| **Floating-Point Math**  | Use `bc -l` for decimal precision              |
| **Positional Variables** | `$1`, `$2`, `$3` used for input parameters     |
| **Escaping Characters**  | In `expr`, `*` must be escaped (`\*`)          |
| **Executable Scripts**   | Use `chmod +x` before running scripts directly |

---

## 🧩 Common Bash Math Techniques

| Expression Type      | Example                | Output      |
| -------------------- | ---------------------- | ----------- |
| Addition             | `$((10 + 5))`          | 15          |
| Subtraction          | `$((10 - 5))`          | 5           |
| Multiplication       | `$((10 * 5))`          | 50          |
| Division (integer)   | `$((10 / 3))`          | 3           |
| Division (float)     | `echo "10/3" \| bc -l` | 3.333333333 |
| Expression with expr | `expr 4 \* 5`          | 20          |

---

## 💡 Notes / Tips

* Always quote `$()` expressions for readability.
* For **floating-point** math, Bash alone isn’t enough — use `bc`.
* `$1`, `$2`, etc. can be used to make one script handle many cases dynamically.
* Escape the asterisk (`\*`) in `expr` to avoid wildcard expansion.
* Use consistent variable naming (e.g., `snake_case`).

---

## ✅ Summary Commands

| Task               | Command                        |
| ------------------ | ------------------------------ |
| Edit a script      | `vi scriptname.sh`             |
| Save changes       | `:wq`                          |
| Make executable    | `chmod +x scriptname.sh`       |
| Run script         | `bash scriptname.sh arg1 arg2` |
| Run with bc        | `echo "expr" \| bc -l`         |
| Escape `*` in expr | `expr 4 \* 5`                  |

---

### 🏁 End of Lab

Successfully completed multiple arithmetic scripting challenges:
✅ Performed integer and float operations in Bash
✅ Used `$1`, `$2`, `$3` for dynamic math
✅ Fixed syntax and operator issues
✅ Created multiple reusable scripts for calculations
