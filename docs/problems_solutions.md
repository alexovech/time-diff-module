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
