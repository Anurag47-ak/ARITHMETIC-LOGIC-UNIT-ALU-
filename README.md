# ARITHMETIC-LOGIC-UNIT-ALU-

COMPANY NAME : CODTECH IT SOLUTIONS

NAME : ANURAG KUMAR

INTERN ID : CT06DF628

DOMAIN : VLSI

DURATION : 6 WEEKS

MENTOR : NEELA SANTOSH

-----DESCRIPTION----

Objective:
The main goal of this task was to design a simple 4-bit ALU (Arithmetic Logic Unit) using Verilog. The ALU was supposed to perform five basic operations — addition, subtraction, bitwise AND, OR, and NOT. I had to write the code for the ALU, create a testbench to verify its working, and generate simulation results to check if it was working as expected.

Introduction:
An ALU is one of the most important components in any digital system or processor. It’s the part that handles all the arithmetic and logical operations. Since I’m just getting started with VLSI design and HDL coding, this was a great opportunity to understand how a basic ALU works internally and how to build one using Verilog.
This task helped me get hands-on experience with digital design, use of behavioral modeling, and how to write and test Verilog code in a simulator.

Design Details:
I designed the ALU in such a way that it takes two 4-bit inputs `A` and `B`, and based on a 3-bit control signal `sel`, it performs one of the following operations:

| Operation   | Control Input (`sel`) |
| ----------- | --------------------- |
| Addition    | `000`                 |
| Subtraction | `001`                 |
| Bitwise AND | `010`                 |
| Bitwise OR  | `011`                 |
| Bitwise NOT | `100` (only on A)     |

The output is stored in a 4-bit register called `result`. I used a `case` statement inside an `always` block to select the operation depending on the value of `sel`.

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

Testbench and Simulation:
To check whether my ALU was working correctly, I wrote a testbench that applied different inputs to `A`, `B`, and `sel`. I also added `$dumpfile` and `$dumpvars` commands to generate waveform outputs.
Here's the testbench I wrote:

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

Simulation Results:

I used an online simulator and also tried local tools like Icarus Verilog + GTKWave to check the waveform outputs. The simulation results confirmed that each operation was giving the expected result. Here's a table of what I observed:

| Operation   | A    | B    | Result |
| ----------- | ---- | ---- | ------ |
| Addition    | 0101 | 0011 | 1000   |
| Subtraction | 0101 | 0011 | 0010   |
| AND         | 0101 | 0011 | 0001   |
| OR          | 0101 | 0011 | 0111   |
| NOT (on A)  | 0101 | —    | 1010   |

The results matched the expected binary outputs perfectly, which confirmed that my ALU was working correctly for all the operations.

Conclusion:
This was my first real digital design task using Verilog, and I learned a lot from it. I got to understand how ALUs work at a hardware level and how to write clean and testable Verilog code. I also learned how to write a testbench and simulate my design to verify its functionality. This task was a great starting point and I’m excited to take on more complex designs in the coming weeks of my internship.

