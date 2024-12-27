# OS Process Scheduling Project 

## Overview
This Java project simulates the process scheduling algorithms used in operating systems. It uses **Swing** for the graphical user interface (GUI) and the **FlatLaf** library for modern UI styling. Users can input processes with their respective CPU times, select a scheduling algorithm, and calculate the waiting and turnaround times.

---

## Features:
- **GUI with FlatLaf Library**: Provides an intuitive interface with light/dark themes.
- **Dynamic Process Management**: Add and remove processes dynamically.
- **Scheduling Algorithms**: 
  - **FCFS (First-Come, First-Served)**
  - **SJF (Shortest Job First)**
  - **Priority Scheduling**
  - **Round Robin**

---

## UI Components
- **Input Fields**:
  - **CPU Time**: For entering CPU times of processes.
  - **Process Number**: A field to represent the process ID.
- **Buttons**:
  - **Add Process**: Adds processes to the table.
  - **Run Algorithm**: Executes the selected scheduling algorithm.
  - **Clear**: Clears the table and resets the process counter.
- **Dropdown (JComboBox)**: Selects the algorithm (FCFS, SJF, etc.).
- **Table (JTable)**: Displays processes, Number of process, CPU time, waiting time, and turnaround time.
- **Message Box**: Displays the average **Waiting Time** and **Turnaround Time** after executing the selected algorithm.

---

## Scheduling Algorithms
### 1. FCFS (First-Come, First-Served)
- Processes are executed in the order they arrive.
- **Waiting time** for each process is calculated by accumulating CPU times of prior processes.

### 2. SJF (Shortest Job First)
- Processes are sorted by CPU time, with the shortest jobs executed first.
- **Waiting time** and **turnaround time** are calculated after sorting.

### 3. Priority Scheduling
- Users manually assign a priority to each process.
- Processes are executed based on their priority.
- **Waiting time** and **turnaround time** are calculated accordingly.

### 4. Round Robin
- Each process is assigned a fixed quantum time for execution.
- If a process is not completed in one cycle, it is placed back in the queue.
- **Waiting time** and **turnaround time** are calculated based on these cycles.

---

## Data Handling
- **Model**: The `DefaultTableModel` is used to handle table data, representing processes and their computed times.
- **Calculation**: The system calculates **waiting time** and **turnaround time** after running the selected algorithm.
- **Average Times**: After the algorithm runs, the average waiting time and turnaround time are displayed in a message box.

---

## Libraries Used
- **FlatLaf**: Provides a modern UI design with light/dark themes.
- **Swing**: Java's GUI toolkit used for components like tables, buttons, and text fields.
- **Java Collections**: Used for sorting and managing processes in the SJF and Priority Scheduling algorithms.

---

## Workflow
1. **Add processes** to the table with CPU times.
2. **Select scheduling algorithm** (FCFS, SJF, Priority, Round Robin).
3. **Calculate waiting time and turnaround time** for each process.
4. **Display results**: Average waiting time and turnaround time in a message box.
5. **Clear** to start with new processes.

---

## Example:
- **Input**: Process 1 with a CPU time of 5 and Process 2 with a CPU time of 10.
- **FCFS Output**:
  - Process 1: Waiting time = 0, Turnaround time = 5
  - Process 2: Waiting time = 5, Turnaround time = 15

---

## Conclusion
This project demonstrates the use of scheduling algorithms with a user-friendly GUI. It provides a great learning tool for understanding how processes are managed in an operating system.


---

# CPU Scheduling Algorithms

## Introduction
CPU scheduling is the foundation of multiprogramming operating systems. It determines how processes share CPU time, similar to managing a busy restaurant where you must decide which customer (process) gets served next and for how long.

## Core Scheduling Algorithms

### 1. First-Come, First-Served (FCFS) 🎟️
**The Simple Queue Master**

#### Description
- Processes are executed in order of arrival (FIFO queue)
- Non-preemptive: process runs to completion once started
- Implementation uses a simple FIFO queue mechanism

#### Example Scenario
```
Processes: P1 (24ms), P2 (3ms), P3 (3ms)
Order: P1 → P2 → P3
Average Waiting Time = 17ms
Average Turnaround Time = 27ms
```

#### Advantages & Disadvantages
✅ **Pros:**
- Simple to understand and implement
- Fair in a basic "first-come" sense

❌ **Cons:**
- Poor performance for interactive systems
- High average waiting times
- Convoy effect (short processes stuck behind long ones)
- Not suitable for time-sharing systems

---

### 2. Shortest Job First (SJF) ⚡
**The Speed Optimizer**

#### Description
- Selects process with shortest CPU burst time
- Can be either preemptive (SRTF) or non-preemptive
- Uses prediction for burst times (exponential averaging)

#### Example Scenario
```
Processes: P1 (6ms), P2 (8ms), P3 (7ms), P4 (3ms)
Average Waiting Time:
- Non-preemptive: 7ms
- Preemptive (SRTF): 3ms
```

#### Advantages & Disadvantages
✅ **Pros:**
- Optimal average waiting time
- Best throughput for short processes

❌ **Cons:**
- Potential starvation of longer processes
- Difficult to implement (future burst prediction needed)
- Not always practical in real systems

---

### 3. Round Robin (RR) 🔄
**The Fair Share Champion**

#### Description
- Fixed time quantum (typically 10-100ms)
- Preemptive: process moves to queue end after quantum expires
- Fair CPU distribution among all processes

#### Key Considerations
- Time quantum selection is crucial:
  - Large quantum → behaves like FCFS
  - Small quantum → excessive context switching
- Optimal: 80% of CPU bursts should be shorter than quantum
- Context switch time should be << quantum

#### Advantages & Disadvantages
✅ **Pros:**
- Fair CPU distribution
- Ideal for interactive systems
- No process starvation
- Good response time

❌ **Cons:**
- Higher average turnaround time than SJF
- Performance heavily depends on quantum size
- Context switching overhead

---

### 4. Priority Scheduling 🎯
**The VIP Manager**

#### Description
- Each process assigned a priority number (lower = higher priority)
- Available in both preemptive and non-preemptive variants
- CPU allocated to highest-priority process

#### Example Configuration
```
Process | Arrival Time | Burst Time | Priority
P1      | 0           | 4          | 1
P2      | 1           | 3          | 3
P3      | 2           | 1          | 4
P4      | 3           | 5          | 2
```

#### Handling Starvation
- Problem: Low-priority processes may never execute
- Solution: Aging – gradually increase priority of waiting processes
- Alternative: Combine with Round Robin for same-priority processes

---

### 5. Multilevel Queue 📚
**The Class System**

#### Structure
- Multiple queues for different process types
- Each queue has its own scheduling algorithm
- Fixed priorities between queues

#### Common Queue Hierarchy
1. Real-time processes (Highest Priority)
2. System processes
3. Interactive processes
4. Batch processes (Lowest Priority)
    
---

### 6. Multilevel Feedback Queue 🔄📚
**The Dynamic Classifier**

#### Implementation
- Multiple priority queues
- Processes can move between queues
- New processes start in highest priority queue
- Uses aging to prevent starvation

#### Example Configuration
```
Queue 0: RR with quantum = 8ms
Queue 1: RR with quantum = 16ms
Queue 2: FCFS
```

## Performance Metrics & Considerations

### Key Metrics
1. CPU Utilization (%)
2. Throughput (processes/time)
3. Turnaround Time (completion - arrival)
4. Waiting Time (time in ready queue)
5. Response Time (first response - submission)

### Algorithm Selection Guide
- **FCFS**: Simple batch systems
- **SJF**: When job lengths are predictable
- **RR**: Interactive and time-sharing systems
- **Priority**: Systems with clear task hierarchy
- **Multilevel**: Mixed workload environments

## Best Practices
1. Match algorithm to system requirements
2. Consider overhead costs
3. Balance fairness and efficiency
4. Monitor and adjust parameters
5. Implement aging where starvation is possible
