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

1.Open a new project using Quartus II.

2.Declare the inputs and outputs inside module projname().

3.Set the reset value using register.

4.Use commands like begin and end to stimulate the counter.

5.For Up counter increment the count and for Down counter decrement the count.

6.End the verilog programming.

### PROGRAM 
```
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: KEERTHANA S
RegisterNumber:  212222230066

UP COUNTERS CODE:
module upcounters(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
	A[3]=(((A[0])&(A[1])&(A[2]))^A[3]);
	A[2]=(((A[0])&(A[1]))^A[2]);
	A[1]=(A[0])^A[1];
	A[0]=A[0]^1;
end
endmodule


DOWN COUNTERS CODE:
module downcounters(clk,A);
input clk;
output reg [3:0]A;
always@(posedge clk)
begin
	A[3]=(((~A[0])&(~A[1])&(~A[2]))^A[3]);
	A[2]=(((~A[0])&(~A[1]))^A[2]);
	A[1]=(~A[0])^A[1];
	A[0]=(~A[0])^1;
end
endmodule
```


### RTL LOGIC UP COUNTER AND DOWN COUNTER  
UP COUNTER RTL FORM:

![p 1](https://github.com/Keerthanasampathkumar/Exp-7-Synchornous-counters-/assets/119477890/274ef4fc-3e47-4c2a-adea-7756cd04b461)

DOWN COUNTER RTL FORM:

![p 2](https://github.com/Keerthanasampathkumar/Exp-7-Synchornous-counters-/assets/119477890/e6351a4f-db44-4227-b77a-516888b842c8)

### TIMING DIGRAMS FOR COUNTER  
UP COUNTER WAVEFORM:
![s 1](https://github.com/Keerthanasampathkumar/Exp-7-Synchornous-counters-/assets/119477890/359125bb-b45c-4049-8fc9-96e8ae9addc0)
DOWN COUNTER WAVEFORM:
![s 2](https://github.com/Keerthanasampathkumar/Exp-7-Synchornous-counters-/assets/119477890/f9f47a8e-cfea-4f1a-87f6-377410564581)

### TRUTH TABLE 
UP COUNTER TRUTH TABLE: 
![t 1](https://github.com/Keerthanasampathkumar/Exp-7-Synchornous-counters-/assets/119477890/ae5d8162-947a-42de-99d5-03f988ead6bd)

DOWN COUNTER TRUTH TABLE:
![t 2](https://github.com/Keerthanasampathkumar/Exp-7-Synchornous-counters-/assets/119477890/c4f47f27-850c-4087-9eee-e22cc496d98c)

### RESULTS 
Thus Synchornous counters up counter and down counter circuit are studied and the truth table for different logic gates are verified.
