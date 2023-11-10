# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter

### Procedure

1.Set the input as clock.

2.Register the output of 4 bit.

3.Use Posedge on the input clock.

4.For Up counter use AND and OR gates to declare the value of each bit.

5.For Down counter use AND, OR and NOT gates to declare the value of each bit.

6.End the module.


### PROGRAM 

/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.

Developed by: SANJAY T

RegisterNumber: 212222110039 
*/

## UP COUNTER:

```
module EXP6(clk,A);
input clk;
output reg [3:0]A;
always@(posedge clk)
begin
A[3]=((A[2]&A[1])&A[0])^A[3];
A[2]=(A[1]&A[0])^A[2];
A[1]=(A[0]^A[1]);
A[0]=1^A[0];
end
endmodule

```

## DOWN COUNTER:

```
module d6(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
A[3]=((~A[2])&(~A[1])&(~A[0]))^A[3];
A[2]=((~A[1])&(~A[0]))^A[2];
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule
```

### RTL LOGIC UP COUNTER AND DOWN COUNTER  

## UP COUNTER:

![image](https://github.com/DINESH18032004/Exp-7-Synchornous-counters-/assets/119477784/8faef9e2-d96f-4100-baf2-c10e7046d866)


## DOWN COUNTER:

![image](https://github.com/DINESH18032004/Exp-7-Synchornous-counters-/assets/119477784/1d98e571-1272-451f-b775-bb7c0125da90)





### TIMING DIGRAMS FOR COUNTER  

## UP COUNTER:

![image](https://github.com/DINESH18032004/Exp-7-Synchornous-counters-/assets/119477784/1d804c1c-14d1-49a4-8556-9ae4d3e2b6a8)

## DOWN COUNTER:


![image](https://github.com/DINESH18032004/Exp-7-Synchornous-counters-/assets/119477784/e1a5fef7-9ec0-4596-85a3-7fc41b305a9d)



### TRUTH TABLE 

![image](https://github.com/DINESH18032004/Exp-7-Synchornous-counters-/assets/119477784/1f231209-d727-479d-8868-8723f1f240f4)


![image](https://github.com/DINESH18032004/Exp-7-Synchornous-counters-/assets/119477784/64486bc2-747f-4dcc-945c-88eb4144140e)



### RESULTS 

Thus the program has been executed successfully.
