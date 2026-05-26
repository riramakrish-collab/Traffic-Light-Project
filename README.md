# Traffic Signal Controller 🚦
 
A demand-based digital traffic signal controller built from scratch using logic gates and D flip-flops. This was one of my ECE labs at Rutgers, and honestly, one of the more satisfying ones. You get to plug your circuit into an actual traffic light at the end.
 
---
 
## What It Does
 
Controls an intersection between a main road and a crossroad. The main road stays green by default. When someone presses the pedestrian "Walk" button, it kicks off a timed sequence through all four states before resetting.
 
---
 
## The State Machine
 
Designed a 2-bit FSM with four states:
 
| State | Output | What's happening | Time |
|---|---|---|---|
| S0 | 00 | Main road green, crossroad red | Waits for walk button |
| S1 | 01 | Main road amber | 4 seconds |
| S2 | 10 | Main road red, crossroad green | 8 seconds |
| S3 | 11 | Crossroad amber | 4 seconds |
 
![State Diagram](assets/Traffic%20State%20Diagram.png)
 
---
 
## Circuit Design
 
Next-state and output logic built using AND, OR, and NOT gates. Two D flip-flops store the current state. An LM555 timer IC generates the clock, the timing is set by resistors and capacitors connected to it.
 
![Circuit Schematic](assets/Traffic%20Circuit%20Diagram.png)
 
---
 
## The Build
 
Implemented everything on a breadboard with discrete logic gate ICs. Active-low outputs connect to the traffic light signals.
 
![Breadboard](assets/Traffic%20Circuit.png)
 

 
![Traffic Light](assets/Traffic%20Signal.png)
 
---
 
## Honest Reflection
 
Getting the sequential logic to work was the hardest part. The circuit wasn't cycling through states correctly at first — I'm pretty sure it was a wiring error somewhere in the flip-flop section. Learned that testing each subsystem independently (clock first, then state machine, then outputs) is the right approach instead of trying to debug everything at once.
 
Also thought about what happens if there's a power interruption, if the state machine resets randomly you could end up with two green lights on at the same time, which is obviously a problem. The fix would be to default to all-red after power is restored, then resume normal operation.
 
---
 
## Stack
 
`Digital Logic` `D Flip-Flops` `LM555 Timer` `Combinational Logic` `FSM` `Breadboard`
