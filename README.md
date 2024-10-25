# Treasure Quest: The Straw Hat Crew!
### COL106 Assignment 3
### September 2024

## Table of Contents
### 1. Background
### 2. Modelling
* Definitions
* State of the System
* Scheduling Policy
* Example
### 3. Requirements
* Heap
* StrawHatTreasury
### 4. Clarifications
### 5. Submission
## Background
In this assignment, we explore a scheduling problem inspired by the adventures of the **Straw Hat Pirates**. The crew has accumulated a vast treasure collection during their journey, and as the Treasurer, it’s your responsibility to ensure the treasure is efficiently managed.

Each crew member can work on only one piece of treasure at a time, and they must carefully prioritize their workload to ensure timely processing of all treasures. This project models the management of this treasure in a way that balances the load among crew members while optimizing for processing time and priority.

The goal is to organize and schedule the treasure management tasks to ensure smooth sailing as the Straw Hat crew continues their adventure toward the **One Piece**.

## Modelling
This project models the treasure management task of the Straw Hat crew as a scheduling problem involving multiple crewmates. Each crewmate processes treasures one at a time, and the system must assign new treasures efficiently based on the load on each crewmate.

## Definitions
* **m**: Number of crewmates available to manage the treasure.
* **Treasure ID (id_j)**: A unique positive integer that identifies each piece of treasure.
* **Treasure Size (size_j)**: The amount of time required to process the treasure. For example, if size_j = 5, it takes 5 units of time to complete.
* **Arrival Time (arrival_j)**: The time when the treasure becomes available for processing. If arrival_j = 7, it can only be processed after time 7.
## State of the System
At any given time t:

* Each crewmate maintains a priority queue of treasure pieces assigned to them.
* The remaining size of a treasure piece j is determined by:
### Remaining Size = Original Size(size_j)-Processed Time


* The load on a crewmate is defined as the total remaining size of the treasures in their queue.
* Note: At any time, a crewmate can only process one piece of treasure.
## Scheduling Policy
When a new piece of treasure arrives, the following policies are applied:

* **Treasure Assignment**: The newly arrived treasure is assigned to the crewmate with the least load, i.e., the smallest total remaining size of all assigned treasures. If multiple crewmates have the least load, the treasure can be assigned to any of them.
* **Treasure Processing**: At time t, each crewmate processes the treasure j with the highest priority:
### Priority(j)= Wait Time(j)- Remaining Size(j)
Where **Wait Time(j)=t-arrival_j**
​
 
If multiple treasures have the same maximum priority, the one with the smallest ID is processed.
## Example
Imagine a scenario where three crewmates manage four pieces of treasure, represented in a flow diagram (refer to the starter code or assignment handout for the diagram).

## Requirements
### Heap
You are required to implement a heap from scratch in the file heap.py. The heap must support any general comparison function, with the following specifications:

**_init_**: Initializes the heap with a time complexity of O(n).

**insert**: Inserts a new element into the heap with time complexity O(log n).

**extract**: Removes and returns the top element with time complexity O(log n).

**top**: Returns the top element without removing it with time complexity O(1).

### StrawHatTreasury
In the file **straw_hat.py**, you must implement the **StrawHatTreasury class**. Here are the specifications:

**_init_**: Initializes the treasury and crewmates, with a time complexity of at most O(m).

**add_treasure**: Adds a treasure and schedules it for processing. Time complexity is O(log n + log m).

**get_completion_time**: Returns a list of treasures in the order of their completion. The time complexity is O(n(log n + log m)).

## Clarifications
* You are allowed to cross-import between the files provided but cannot import additional libraries.
* The use of hash-based data structures such as dictionaries and sets is prohibited. You must implement a heap using an array-based approach.
* Treasure size and arrival time can be arbitrarily large, but the time complexity of your solution should not depend on these values.
* You may use the inbuilt Python sort function only for sorting the output of the get_completion_time method.
* The recursion limit should not be a concern as long as your code runs within the expected time complexity.
