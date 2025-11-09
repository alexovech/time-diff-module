### Problem 1 - Invalid BCD Output (>9)

**Problem Description:**
In this circuit, during testing, the subtraction sometimes gave results greater than 9, which is invalid in BCD format-for example, 1010₂.
This occurred because carry propagation between adders produced binary sums that exceeded the range of allowed BCD.

**Solution Implemented:**
To rectify this, an extra **Full Adder (SN74LS283)** was implemented to carry out a BCD correction (+6) when the output exceeded 1001₂.

**The principle of working:**
The AND and OR gates formed the detection logic, which would identify when bits D3 and D1 were simultaneously equal to '1', among other combinations of overflows; this created a correction trigger signal.
How It Works Now:
The output from the previous adder forms an invalid BCD pattern (> 1001₂).
the correction logic is triggered, which sends a binary `1010₂` (+6) into the input of the additional adder.
This adder adjusts the value to return it to the valid BCD range of 0 to 9. The correction stage receives `0000₂` if the condition for overflow is false; this leaves the output unchanged. Consequently, every digit remains a valid BCD output irrespective of the carry propagation during subtraction.


--

### Problem 2 - Incorrect Display of Negative Results

**Problem Description:**
In those cases where the subtrahend was larger than the minuend, there was an invalid BCD result, for instance, “997” produced from the subtraction circuit instead of indicating a negative result "003".
In addition, there was no logic related to handling negative values or borrowing in the system.

**Solution Implemented:**
A fourth last Full Adder (SN74LS283), along with a few XOR gates (SN74LS136), was added to check if the result obtained after subtraction was negative.
The XOR phase was receiving signals from both the final **carry-out** signal and the error detection AND gate series. 

**The principle of working:**
Both signals' negative result indicators would cause the XOR gates to invert bits.
As soon as the system recognizes a borrow or an absent carry (logic ‘1’ from detection gates), the XOR function reverses its output bits. As a result, the two’s complement negative value gets transformed into its positive magnitude. Accordingly, instead of printing an invalid number (like 997), the result is corrected to print a valid representation of its absolute value in BCD. The sign itself isn’t shown, but the numerical value remains correct and fixed within the 7-segment display.
