### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**
This Verilog program describes a 4-bit synchronous up-counter.

The counter increases its value by 1 on every positive edge of the clock.

When reset (rst) = 1, the counter output becomes 0 immediately on the next clock edge.

When reset = 0, normal counting continues: 0,1,2,…,15, then it rolls over to 0 again.
The design uses a non-blocking assignment (<=) for sequential logic.
**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**
```
Compile the Verilog code in Quartus.

Open University Program VWF (File → New → University Program Waveform File).

Insert the signals (clk, rst, out[3..0]) into the waveform.

Create a clock for clk (Right-click clk → Insert Clock → 20 ns period).

Set rst = 1 for the first few clock cycles, then change to 0.

Save the VWF and run Simulation (Assignments → Simulation → Run).

Observe the output counting sequence (0000, 0001, 0010, …).
```

**PROGRAM**
```
module ex11(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out+1;
end
endmodule
```

Developed by:Samantha Shree S.V 
RegisterNumber:25017585
*/

**RTL LOGIC UP COUNTER**
<img width="1920" height="1080" alt="Screenshot (106)" src="https://github.com/user-attachments/assets/d63d9f22-e22e-4b36-8a88-98b7ed77c4b0" />

**TIMING DIAGRAM FOR IP COUNTER**
<img width="1920" height="1080" alt="Screenshot (107)" src="https://github.com/user-attachments/assets/936cc1a8-a03d-4e0d-b264-4fe212788590" />

**TRUTH TABLE**
![ex11 truth](https://github.com/user-attachments/assets/49e1a9d0-b3a9-41e9-98e7-2594d61e5276)

**RESULT**
Thus 4 bit synchronous up counter and validate functionality is executed.
