# OS Process Scheduling Project 

## Overview
This Java project simulates the process scheduling algorithms used in operating systems. It uses **Swing** for the graphical user interface (GUI) and the **FlatLaf** library for modern UI styling. Users can input processes with their respective CPU times, select a scheduling algorithm, and calculate the waiting and turnaround times.

## Features:
- **GUI with FlatLaf Library**: Provides an intuitive interface with light/dark themes.
- **Dynamic Process Management**: Add and remove processes dynamically.
- **Scheduling Algorithms**: 
  - **FCFS (First-Come, First-Served)**
  - **SJF (Shortest Job First)**
  - **Priority Scheduling**
  - **Round Robin**

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

## Data Handling
- **Model**: The `DefaultTableModel` is used to handle table data, representing processes and their computed times.
- **Calculation**: The system calculates **waiting time** and **turnaround time** after running the selected algorithm.
- **Average Times**: After the algorithm runs, the average waiting time and turnaround time are displayed in a message box.

## Libraries Used
- **FlatLaf**: Provides a modern UI design with light/dark themes.
- **Swing**: Java's GUI toolkit used for components like tables, buttons, and text fields.
- **Java Collections**: Used for sorting and managing processes in the SJF and Priority Scheduling algorithms.

## Workflow
1. **Add processes** to the table with CPU times.
2. **Select scheduling algorithm** (FCFS, SJF, Priority, Round Robin).
3. **Calculate waiting time and turnaround time** for each process.
4. **Display results**: Average waiting time and turnaround time in a message box.
5. **Clear** to start with new processes.

## Example:
- **Input**: Process 1 with a CPU time of 5 and Process 2 with a CPU time of 10.
- **FCFS Output**:
  - Process 1: Waiting time = 0, Turnaround time = 5
  - Process 2: Waiting time = 5, Turnaround time = 15

## Conclusion
This project demonstrates the use of scheduling algorithms with a user-friendly GUI. It provides a great learning tool for understanding how processes are managed in an operating system.



