# LabVIEW 4-Digit Armstrong Number Check

## Overview
A LabVIEW VI demonstrating **While Loop**, **Shift Register**, **Quotient & Remainder**, **Compound Arithmetic**, and arithmetic operations to determine whether a **4-digit number** is an Armstrong number.

## Level
**LabVIEW Fundamentals – Level 1**

## Input
- **Number Under Test** — User-provided 4-digit integer.

## Processing
1. The input number is provided to the While Loop.
2. The VI extracts individual digits using **Quotient & Remainder** with 10.
3. The remainder provides the current digit.
4. The quotient becomes the number for the next loop iteration.
5. Each extracted digit is raised to the **4th power**.
6. A **Shift Register** maintains the running sum of the calculated values.
7. The loop continues until the quotient becomes 0.
8. The final calculated value is compared with the original input number.

## Output
- **Calculated Armstrong Value** — Sum of the fourth powers of the extracted digits.
- **Armstrong Check Result** — TRUE when the calculated value equals the original 4-digit input; otherwise FALSE.

## Examples

### Armstrong Number
For input **1634**:

`1⁴ + 6⁴ + 3⁴ + 4⁴ = 1634`

**Result: TRUE**

For input **9474**:

`9⁴ + 4⁴ + 7⁴ + 4⁴ = 9474`

**Result: TRUE**

### Non-Armstrong Number
For input **1234**:

`1⁴ + 2⁴ + 3⁴ + 4⁴ = 354`

**Result: FALSE**

## LabVIEW Concepts Demonstrated
- While Loop
- Shift Registers
- Quotient & Remainder
- Compound Arithmetic
- Numeric Operations
- Boolean Comparison
- Loop Termination Logic
- Front Panel and Block Diagram design

## Project Files
- `Armstrong_Number_Check.vi` — Main VI
- `LabVIEW_Armstrong_Number.lvproj` — LabVIEW Project
- `README.md` — Project documentation
