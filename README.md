# Design specification

Move the elevator either up or down to reach the requested floor. Once at the requested floor, open the door for at least 2 seconds. Ensure the door is never open while moving. 
Don’t change directions unless there are no higher requests when moving up or no lower requests when moving down. Assume that the elevator moves from one floor to another in 2 seconds. 
The controller should use the 50 MHz clock on DE0-CV board. Use a 1 sec clock enable to the timer for the elevator movement and the opening of the door. 
The inputs and outputs of the controller are shown in the figure below. Also, the controller can be broken into a Request Resolver that resolves various floor requests into single requested floor 
and a Unit Control that moves elevator to this requested floor. Design the controller to serve up to 10 floors (0 is the ground floor and 9 is the highest floor). Use SystemVerilog Parameters 
for the number of floors. The floor output should be connected to a seven segment display through a binary to SSD converter.

# Elevator controller block diagram and interface ports
![Elevator](https://github.com/user-attachments/assets/8fb5f118-7ec4-4396-8681-216bf713cef0)

Test cases verified on the design as well as synthesization on FPGA 5CEBA4F23C7
These are the most important cases you should to cover them:
1. verify that the elevator moves between floors at 2 seconds. (this should appear in the cases)
2. Verify that the door opens at the requested floor and remains open for at least 2 seconds. (this should appear in the cases)
3. Ensure that the elevator doesn’t change direction unless there are no pending requests in the current direction.
Example: If the elevator is moving up with requests for floors 3, 6, and 8, it should complete all upward requests before changing direction to move down.
4. Request Prioritization: Make sure that requests in the current direction are prioritized. 
Example: If the elevator is at floor 4 and has requests for floors 6, 7, and 3, it should go to floors 6 and 7 first, then go down to floor 3.
5. Test behavior at the lowest and highest floors.
 Example: If the elevator is at floor 0 and receives a request to go down, ensure it does not attempt to go below floor 0 ,Similarly, if at floor 9, a request to go up should not result in movement above floor 9
6. Verify how the system handles multiple requests at once. 
Example: The elevator is at floor 5 with requests for floors 3, 7, 2, and 8. If moving up, it should prioritize floors 7 and 8 before handling lower floors."
7. Immediate Door Open on Same Floor Request, If a request is made for the same floor where the elevator is currently stopped, the door should open immediately without moving, 
Example: The elevator is at floor 5, and someone presses the request button for floor 5. The door should open without the elevator changing its position. ( this is for inside buttons and outside buttons)"
8. Handling Intermediate Requests While Moving: When the elevator is moving to a higher (or lower) floor and a new request is made for an intermediate floor, the elevator should prioritize the intermediate floor before reaching the original destination.
Example: The elevator is at floor 1, heading to floor 4. While moving, a request comes in for floor 3 when the elevator reaches floor 2. The elevator should stop at floor 3 first before continuing to floor 4."
9. Stopping for Combined Internal and External Requests in Sequence as Ensure the elevator responds to both internal and external requests as it moves and stops at each requested floor in sequence. 
Example: The elevator is at floor 2 moving up with internal requests for floors 5 and 8, and external requests to go up from floor 3 and down from floor 6. It should stop at floors 3, 5, 8 then go to 6."
10. Error Handling and it is option for Testing for unexpected conditions, such as requesting a floor outside the elevator’s range or conflicting requests.
Example: The elevator is on floor 3 and receives a request to go to floor 11 (out of range). Ensure the system rejects this request."
Also you can add more test cases if you’d like to cover additional scenarios.

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


