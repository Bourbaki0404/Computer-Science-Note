# Microarchitecture
<img src="images/micro.png">
<img src="images/trade_off1.png">

- we update the state during the execution, but only update architectural state at the end of an instruction execution.

- In multi-cycle processor, the cycle time is determined by the slowest stage.

- Each stage can take multiple clock cycle to complete. For example, the execution stage may take 5 cycles, while instruction decoding may takes only 2.
<img src="images/single_cycle_vs_mulcycle.png">

### Design Choices
<img src="images/design_choices.png">

### Several Assumptions in simple processor design
<img src="images/assumptions.png">

- Memory access in reality may takes hundreds of cycles, in which case we need a ready signal to inform us when the data returns from memory.


### Datapath & Control Logic
<img src="images/datapath_control.png">

### Analysis of Single-Cycle Uarch
<img src="images/single_cycle_analysis.png">


- Clock cycle time of microarch is determined by the slowest instruction.
- In real world, memory access is the slowest, which might takes more than 100 ns.
- If we let all instructions take that long time, the performance of processor will be severely limited.

### Drawbacks of Single-Cycle microarchitecture
<img src="images/complexity.png">

- We will see that single-cycle design indeed violates those critical design priciples in microarchitecture.

### Design Principle of Microarchitecture
<img src="images/principles.png">

- Simplify the combinational logic and introduce multi-cycle stages.
- Optimize those commonly used instructions. However, in the case of single cycle uarch, simple instructions like add cannot be improved, since the cycle time is determined by the slowest instruction.
- Balance the resources to remove bottlenecks.
- Single-Cycle march violates those principles.

### Multicycle Microarchitecture
<img src="images/multicycle.png">

- with the introduction of programmer-invisible state, we can optimize the execution of instruction and update the architectural state at the end of the execution.

### Benefit of Multi-Cycle Microarchitecture
<img src="images/benefit-of_multicycle.png">

- Able to optimize common instructions.
- Can reuse hardware components in one instruction.

### The Drawbacks of Multicycle-Uarch
- Hardware overhead for state elements.
- Register setup/hold time overhead paid multiple times in single instruction.

### Implementation of Multicycle-Uarch
<img src="images/multicycle_imp1.png">
<img src="images/multicycle_imp2.png">

- Divide instruction processing cycle into multiple steps.
- Each step corresponde to a state.
- Use FSM to control the sequence of state. Each state defined by the control signals.

### Multicycle Processor Features
<img src="images/multicycle-mips.png">

- longest instruction takes many cycles, while simple instruction can be really fast.

- If memory are not ready, then stay in the "memory access" state until it returns the data.

![](images/optimization_target.png)

### FSM Controller
<img src="images/state_machine_mips.png">



### Lack of Concurrency
<img src="images/lack_of_concurrency1.png">

- Some hardware resources are idle during different stages of instruction processing cycle. For example, the execution unit is idle when an instruction is being decoded.

- Only one instruction executed in a instruction processing cycle.

- Why not arrange multiple instructions on different stages in multicycle microarchitecture?

### Improve Concurrency
<img src="images/improve_concurrency.png">

- Let multiple instructions to be processed together.
- When an instruction is using some resources, process other instruction on idle resources not needed by that instruction.
- We can multiplex the hardware to bring more parallelism.
- More concurrency means higher throughput.

### Basic Idea of Pipelining
<img src="images/lack_of_concurrency.png">

### Ideal Pipeline
![](images/ideal_pipeline.png)

### Performance Calculation
![](images/performance_calculation.png)

### Issues in Pipelining
![](images/not_ideal_pipeline.png)
- 
- 
- 
![](images/issue_in_pipeline.png)


### Multithreading
<img src="images/idea_pipeline.png">

![](images/multithreading.png)

### Analysis of Multithreading
![](images/multithreading_analysis.png)