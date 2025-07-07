# ARITHMETIC-LOGIC-UNIT-ALU-

COMPANY NAME : CODTECH IT SOLUTIONS

NAME : ANURAG KUMAR

INTERN ID : CT06DF628

DOMAIN : VLSI

DURATION : 6 WEEKS

MENTOR : NEELA SANTOSH

-----DESCRIPTION----

Objective:
The objective of this internship task was to design and implement a **Basic Arithmetic Logic Unit (ALU)** using **Verilog HDL**. The ALU was required to perform **five basic operations**: Addition, Subtraction, Bitwise AND, Bitwise OR, and Bitwise NOT. The goal was to understand fundamental digital design concepts, practice hardware description languages (HDL), and verify the design through simulation using a testbench.

Introduction:
An Arithmetic Logic Unit (ALU) is one of the most essential components of a CPU or microprocessor. It performs arithmetic operations (like addition and subtraction) and logic operations (like AND, OR, and NOT). Designing an ALU is considered a foundational exercise in digital electronics and VLSI, especially for engineering students in the ECE or CS domain.
This task gave me the opportunity to work hands-on with Verilog HDL, understand the behavioral modeling of digital circuits, and simulate real hardware operations using software tools.

Design Specifications:

The ALU was designed to support the following 5 operations:

| Operation   | Control Input (`sel`)   |
| ----------- | ----------------------- |
| Addition    | `000`                   |
| Subtraction | `001`                   |
| Bitwise AND | `010`                   |
| Bitwise OR  | `011`                   |
| Bitwise NOT | `100` (only on input A) |

The ALU accepts two 4-bit inputs (`A` and `B`) and produces a 4-bit result based on the 3-bit select input (`sel`). A simple case-based control structure was used to perform different operations based on the value of `sel`.

Verilog Code:

```verilog
module ALU (
    input [3:0] A,
    input [3:0] B,
    input [2:0] sel,
    output reg [3:0] result
);

always @(*) begin
    case (sel)
        3'b000: result = A + B;
        3'b001: result = A - B;
        3'b010: result = A & B;
        3'b011: result = A | B;
        3'b100: result = ~A;
        default: result = 4'b0000;
    endcase
end

endmodule
```

This code is written using **behavioral modeling** in Verilog and represents how the ALU reacts to changes in inputs using a combinational `always` block.

Testbench and Simulation:

To verify the functionality of the ALU, a testbench was written. The testbench provides stimulus to the ALU module by applying different combinations of inputs and select lines. Here's a portion of the testbench code:

```verilog
module ALU_tb;

reg [3:0] A, B;
reg [2:0] sel;
wire [3:0] result;

ALU uut (
    .A(A),
    .B(B),
    .sel(sel),
    .result(result)
);

initial begin
    $dumpfile("wave.vcd");
    $dumpvars(0, ALU_tb);

    A = 4'b0101; B = 4'b0011; sel = 3'b000; #10; // Addition
    sel = 3'b001; #10;                          // Subtraction
    sel = 3'b010; #10;                          // AND
    sel = 3'b011; #10;                          // OR
    sel = 3'b100; #10;                          // NOT

    $finish;
end

endmodule
```

---

Simulation Results:

The simulation was performed using tools like EDA Playground or Icarus Verilog with GTKWave. The results were verified through the generated VCD waveform, which confirmed that each operation was producing correct outputs. Below is the observed output for each operation:

| sel (Operation) | Input A | Input B | Output (Result) |
| --------------- | ------- | ------- | --------------- |
| 000 (Add)       | 0101    | 0011    | 1000 (8)        |
| 001 (Subtract)  | 0101    | 0011    | 0010 (2)        |
| 010 (AND)       | 0101    | 0011    | 0001 (1)        |
| 011 (OR)        | 0101    | 0011    | 0111 (7)        |
| 100 (NOT)       | 0101    | —       | 1010 (\~A)      |

These results matched the expected behavior of an ALU and validated the design.

Conclusion:

This task provided valuable practical experience in hardware design and HDL coding. By designing a 4-bit ALU in Verilog, I learned how to structure a combinational logic circuit, how to use `case` statements for control logic, and how to verify a digital design using a testbench and simulation tools. It also gave me insight into debugging, waveform analysis, and how actual logic operations are implemented inside a processor.

This foundational task sets the stage for more complex digital systems like multiplexers, counters, finite state machines (FSMs), and full processors, which I hope to explore in the upcoming stages of my internship.

