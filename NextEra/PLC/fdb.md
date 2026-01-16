# Function Block Diagrams (FBD)
## Contents
[Bit Logic Function Blocks](#bit-logic-function-blocks)
    
- [OR Logic](#or-logic--1)
- [Assignment](#assignment)
- [Negation](#negation)
- [AND Logic](#and-logic)
- [XOR Logic](#xor-logic-exclusive-or)
- [NAND Logic](#nand-logic-not-and)
- [NOR Logic](#nor-logic-not-or)

[Bistable Function Blocks](#bistable-function-blocks)

- [Set/Reset](#setreset)
-
## Bit Logic Function Blocks

Bit logic function blocks are fundamental building blocks in FBD programming that perform basic logical operations on individual binary signals (0/1 or TRUE/FALSE). These blocks form the foundation for control logic, allowing you to combine multiple inputs to make decisions and drive outputs. Common operations include AND, OR, XOR, and their negated variants (NAND, NOR), which enable complex conditional logic to be built from simple, standardized components.

### OR Logic (>= 1)

![Alt text](figures/FBD-OR-Logic.png)

| IN1 | IN2 | OUT |
|:---:|:---:|:---:|
|  0  |  0  |  0  |
|  0  |  1  |  1  |
|  1  |  0  |  1  |
|  1  |  1  |  1  |


### Assignment 
Assigns the input to a place in the PLC memory

![Alt text](figures/FBD-Assignment.png)

### Negation 

Inverts the input or output of a block. 

The small circle in the pin of the block represents the negation. 
Output of the assignment block is negated in the below figure. 

![Alt text](figures/FBD-Negation.png)

Negating means, if the signal was true, it becomes false and vice versa

### AND Logic 

![Alt text](figures/FBD-AND-Logic.png)

| IN1 | IN2 | OUT |
|:---:|:---:|:---:|
|  0  |  0  |  0  |
|  0  |  1  |  0  |
|  1  |  0  |  0  |
|  1  |  1  |  1  |

### XOR Logic (Exclusive OR)

![Alt text](figures/FBD-XOR-Logic.png)

| IN1 | IN2 | OUT |
|:---:|:---:|:---:|
|  0  |  0  |  0  |
|  0  |  1  |  1  |
|  1  |  0  |  1  |
|  1  |  1  |  0  |

### NAND Logic (Not AND)
Negates the output of the AND block

![Alt text](figures/FBD-NAND-Logic.png)

| IN1 | IN2 | OUT |
|:---:|:---:|:---:|
|  0  |  0  |  1  |
|  0  |  1  |  1  |
|  1  |  0  |  1  |
|  1  |  1  |  0  |

### NOR Logic (Not OR)
Negates the inputs of the AND Block 

![Alt text](figures/FBD-NOR-Logic.png)

| IN1 | IN2 | OUT |
|:---:|:---:|:---:|
|  0  |  0  |  1  |
|  0  |  1  |  0  |
|  1  |  0  |  0  |
|  1  |  1  |  0  |

Same as adding a negate circle at the output of the OR block

## Bistable Function Blocks
Bistable function blocks are simple memory elements that hold their output state (ON/OFF, TRUE/FALSE) until actively reset. They maintain their last known state even after input signals change, making them essential for latching operations, emergency stops, and state retention in PLC systems. Common bistable blocks include SR (Set/Reset) and RS (Reset/Set) latches, which differ in priority—SR prioritizes set commands while RS prioritizes reset commands for safety-critical applications.
 
### Set/Reset
Used when start commands take priority
- `S1 = TRUE` --> `Q1 = TRUE`
- `S1 = FALSE` 
    - `R = TRUE` --> `Q1 = FALSE`
    - `R = FALSE` --> `Q1 = TRUE/FALSE`
 
For the condition where `S1 = FALSE` and `R = FALSE`, `Q1` will equal whatever the last value of `Q1` was. This is the "memory" aspect.

![SR Block](figures/FBD-SR-Latch1.png "SR Block")
*SR Block*

![Inside SR Block](figures/FBD-SR-Latch2.png "Inside SR Block")
*Inside SR Block*
|  S1 |  R  | Q1  |
|:---:|:---:|:---:|
|  0  |  0  | 0/1 |
|  0  |  1  |  1  |
|  1  |  0  |  0  |
|  1  |  1  |  1  |

### Reset/Set
Used when stop commands take priority (emergency stop)
- `R1 = TRUE` --> `Q1 = FALSE`
- `R1 = FALSE` 
    - `S = TRUE` --> `Q1 = TRUE`
    - `S = FALSE` --> `Q1 = TRUE/FALSE`

For the condition where `R1 = FALSE` and `S = FALSE`, `Q1` will equal whatever the last value of `Q1` was. This is the "memory" aspect.

![SR Block](figures/FBD-SR-Latch1.png "SR Block")
*SR Block*

![Inside SR Block](figures/FBD-SR-Latch2.png "Inside SR Block")
*Inside SR Block*
|  S  |  R1 | Q1  |
|:---:|:---:|:---:|
|  0  |  0  | 0/1 |
|  0  |  1  |  0  |
|  1  |  0  |  1  |
|  1  |  1  |  0  |

## Edge Detection

## Edge Detection

Edge detection identifies the moment when a signal transitions from one state to another (rising edge: 0→1, or falling edge: 1→0). In PLC programming, edge detection is crucial for triggering actions only once when a condition changes, rather than continuously while the condition is true. This is commonly used in function block diagrams to capture state changes for events like button presses, sensor triggers, or signal transitions that require single-pulse responses.
## Timer Function Blocks

## Counter Function Blocks