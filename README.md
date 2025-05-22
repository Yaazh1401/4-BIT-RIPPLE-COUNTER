# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**
1.Type the program in Quartus software.

2.Compile and run the program.

3.Generate the RTL schematic and save the logic diagram.

4.Create nodes for inputs and outputs to generate the timing diagram.

5.For different input combinations generate the timing diagram.

**PROGRAM**
```
module exp12(
    input wire clk,        
    input wire reset,     
    output wire [3:0] q    
);

    wire clk1, clk2, clk3;
    T_FF tff0 (
        .clk(clk),
        .reset(reset),
        .q(q[0]),
        .clk_out(clk1)
    );

    T_FF tff1 (
        .clk(clk1),
        .reset(reset),
        .q(q[1]),
        .clk_out(clk2)
    );

    T_FF tff2 (
        .clk(clk2),
        .reset(reset),
        .q(q[2]),
        .clk_out(clk3)
    );

    T_FF tff3 (
        .clk(clk3),
        .reset(reset),
        .q(q[3]),
        .clk_out()
    );

endmodule


module T_FF (
    input wire clk,
    input wire reset,
    output reg q,
    output wire clk_out
);
    assign clk_out = q;  // Output to next stage

    always @(negedge clk or posedge reset) begin
        if (reset)
            q <= 0;
        else
            q <= ~q;
    end
endmodule 

```
 Developed by:Yaazhini S 
 RegisterNumber:212224230308


**RTL LOGIC FOR 4 Bit Ripple Counter**

![image](https://github.com/user-attachments/assets/0284daaa-78a8-4ba0-b495-1f6f29b7e95e)




**TIMING DIGRAMS FOR 4 Bit Ripple Counter**

![image](https://github.com/user-attachments/assets/45d7d66b-1bfe-4e21-a2cd-68f530bb3acd)




**RESULTS**
Thus the given 4 Bit Ripple Counter are implemented using verilog and validated their functionality using functional tables are verified in Quartus II.
