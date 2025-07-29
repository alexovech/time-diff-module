# Time Difference Module
Digital time-difference calculator with PCB layout and simulation in Multisim 

# Purpose

Receives two BCD-encoded lap-time values from independent stopwatches—triggered whenever each car (or any moving object) crosses the finish-line sensor—then calculates their difference. It handles carries, corrects invalid BCD digits (>9) by adding 6, detects negative outcomes via the borrow flag, and re-inverts the result when necessary to display a valid absolute Δt. After processing, the final three-digit value is latched before the stopwatches reset and is driven to a seven-segment display, giving an immediate, race-style read-out of how far ahead or behind one competitor is.
