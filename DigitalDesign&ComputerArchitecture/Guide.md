## From Nand Gate 2 Tetris
> Course Website: https://www.coursera.org/learn/build-a-computer/supplement/4DqXs/course-overview

You can switch to the Chinese subtitle.

After watching the first three chapters, you will know:
- The idea of abstraction Levels in computer hierarchy.
- How to build simple boolean and arithmetic unit.
- The explict relationship between combinational logic circuit and boolean function.
- How bits are stored in a state element.
- How sequential logic is constructed by simply adding state unit into combinational logic. 

## Verilog
### Resource
- Tutorial: https://www.runoob.com/w3cnote/verilog-tutorial.html (Chinese version)

- Tutorial: https://vlab.ustc.edu.cn/guide/doc_verilog.html (Chinese version)

- Guidebook: https://www.chipverify.com/verilog/verilog-introduction

### Build flow
To run verilog on your machine, for first you need to install it.
```
 sudo apt install iverilog
```
To convert .v file into simulation, use command
```
 iverilog -o <outputname> <inputname>.v
```
Where \<outputname> represents the name of simulation, and \<inputname> is the name of the  verilog code file. Flag -o means output.

To run a simulation, type in
```
 vpp <outputname>
```
in the terminal. (Don't forget to change to the current directory)

### Task
```
0. Understand structural Verilog and Behavior Verilog.

1. Write a Verilog module to implement a 2-to-1 multiplexer.
2. Create a Verilog module for a full-adder.
3. Write Verilog code to implement a 4-bit binary counter.
4. Implement a 2-bit comparator in Verilog.
5. Write a Verilog module to realize a 4-bit shift register.
6. Create a Verilog module to implement a 3-input AND gate.
7. Implement a 3-to-8 decoder in Verilog.
8. Write Verilog code for a 4-bit magnitude comparator.
9. Implement a 4-bit ripple carry adder in Verilog.
10. Write Verilog code to realize a 4-bit barrel shifter.
11. Create a Verilog module for a 4-bit register file.
12. Implement a 4-bit ALU (Arithmetic Logic Unit) in Verilog.
```
You can ask ChatGPT for assistance whenever feel difficult.

#### Example:
The following code illustrate how to build a xor gate in verilog.
$$C = A\~B + \~A B$$

Structral Verilog:
```verilog 
module xor_gate (
    input a,
    input b,
    output xor_output
);

wire w1, w2, w3;

and_gate and1 (.a(a), .b(~b), .output(w1));
and_gate and2 (.a(~a), .b(b), .output(w2));
or_gate or1 (.a(w1), .b(w2), .output(w3));
assign xor_output = w3;

endmodule

module and_gate (
    input a,
    input b,
    output output
);

assign output = a & b;

endmodule

module or_gate (
    input a,
    input b,
    output output
);

assign output = a | b;

endmodule
```

Behavior Verilog:
```verilog
module xor_(input a, input b, output c); // define the module and its ports.
 assign c = a ^ b;//see verilog operations.
endmodule //every module should be embraced by endmodule directive.
```
