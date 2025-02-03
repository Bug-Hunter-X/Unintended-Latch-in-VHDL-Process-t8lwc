# Unintended Latch in VHDL Process

This repository demonstrates a common error in VHDL: an unintended latch created within a process.  The provided VHDL code implements a simple register, but due to a missing `else` statement in the process, it may behave unexpectedly. The `data_out` signal may retain its previous value instead of updating reliably,  leading to potential design flaws.

The `bug.vhdl` file contains the erroneous code, while `bugSolution.vhdl` demonstrates the corrected implementation, properly handling all conditions to avoid unintended latches.

## How to Reproduce

1. Simulate `bug.vhdl` with various clock and input signals.
2. Observe that `data_out` might not update consistently with `data_in`, particularly when there are changes in the input signal in consecutive clock cycles.
3. Then, compare the behavior with `bugSolution.vhdl` for a clear contrast.

## Solution

The solution involves ensuring that the output signal (`data_out`) is driven in all possible conditions within the process. This is achieved by adding an `else` statement that assigns a default value or handles specific conditions that weren't explicitly handled before. This prevents the unintentional creation of latches in the synthesized hardware.