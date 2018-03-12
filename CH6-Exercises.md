## Total order broadcast (TOB)

1. Causal Order broadcast does not enforce Total order. Give an example for this (sequence diagram).

2. TOB does not implement FIFO or Causal Order. Give an example for this (sequence diagram).

3. In what model can Algorithm 6.1 be used?

### Byzantine total order broadcast (BTOB)

4. Which of the properties from Module 6.1 (regular TOB) cannot be achieved with byzantine faulty nodes?

5. What can go wrong if we replace reliable broadcast in Algorithm 6.1 with their Byzantine variant 
and use weak-byzantine consensus (Module 5.10, p.245) instead of normal consensus?

6. How does Algorithm 6.2 avoid the problems you found in e. above?

## Terminating reliable broadcast (TRB)

7. We replace the perfect failure detector in Algorithm 6.3 with an eventually perfect failure detector,
and the `<CRASH>` even with the `<SUSPECT>` event. 
    * Which properties from Module 6.4 still hold? 
    * Can you reformulate the properties that no longer hold?
  
 ## Fast Consensus
 
 8. Give an example of an execution of Algorithm 6.4, where some process decides on the fast path and 
 another process decides on the slow path.


## Group membership

9. Consider Algorithm 6.9-6.10. Here the algorithm requests from the application to stop sending messages. 
    * What whould happen if instead, the algorithm would simply stop to forward messages? 
      Which property of Module 6.9 or 6.10 would be violated?
10. If we implement Algorithm 6.9-6.10 in the *fail-noisy* model with an eventually perfect failure detector (<>P) and use 
    the `<SUSPECT>` event instead of `<CRASH>`, what properties from Module 6.10 would still hold?
    * How can we handle the failure bound *f* and the `<RESTORE>` events from <>P?
    
## Good execises from the book
I recommend at least reading all exercises from the book. 
The following ones are especially relevant:

* Exercise 6.8
* Exercise 6.9
* Exercise 6.11
* Exercise 6.13
