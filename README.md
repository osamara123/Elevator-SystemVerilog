# Design specification

Move the elevator either up or down to reach the requested floor. Once at the requested floor, open the door for at least 2 seconds. Ensure the door is never open while moving. 
Don’t change directions unless there are no higher requests when moving up or no lower requests when moving down. Assume that the elevator moves from one floor to another in 2 seconds. 
The controller should use the 50 MHz clock on DE0-CV board. Use a 1 sec clock enable to the timer for the elevator movement and the opening of the door. 
The inputs and outputs of the controller are shown in the figure below. Also, the controller can be broken into a Request Resolver that resolves various floor requests into single requested floor 
and a Unit Control that moves elevator to this requested floor. Design the controller to serve up to 10 floors (0 is the ground floor and 9 is the highest floor). Use SystemVerilog Parameters 
for the number of floors. The floor output should be connected to a seven segment display through a binary to SSD converter.

# Elevator controller block diagram and interface ports


# Test Cases Simulation 
![Test_case_1,2](https://github.com/user-attachments/assets/9f2fdd49-cd8b-4678-abe6-0d
![Test_case_5](https://github.com/user-attachments/assets/4688d9c9-b6f8-4a71-af44-170f4bacaa6a)
![Test_case_6](https://github.com/user-attachments/assets/d38e9a95-1dbd-452c-9b9e-3
![FSM](https://github.com/user-attachments/assets/845159b6-6aa5-4bb4-8941-9b6e95686357)
f79e7f50197)
![Test_case_8](https://github.com/user-attachments/assets/891e3bc2-fc64-4309-9194-55dcba45f020)
![Test_case_9](https://github.com/user-attachments/assets/52610aa1-71ed-4673-a81e-50495111f372)
03efd21625)
![Test_case_3,4](https://github.com/user-attachments/assets/50ab2b3b-2284-4073-a2cc-016335380062)


