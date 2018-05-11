## Total order broadcast (TOB)

1. Causal Order broadcast does not enforce Total order. Give an example for this (sequence diagram).

__ANSWER:__ *Assume two messages `m1` and ` m2`are sent concurrently by different processes. Using Causal Order broadcast, they can be deliveded in different order, at different processes, e.g. `p1` delivers first `m1` then `m2`, `p2` delivers first `m2` then `m1`.  This violates Total order.*

2. TOB does not implement FIFO or Causal Order. Give an example for this (sequence diagram).

__ANSWER:__ *Assume `p1` sends first `m1` then `m2`, before delivering `m1`. FIFO and Causal order require that every process delivers `m1` before `m2`but Total order does not guarantee this.*

3. In what model can Algorithm 6.1 be used?

__ANSWER:__ *In all models with crash failures, where we can solve consensus, i.e. fail-stop, fail-noisy and randomized.*

### Byzantine total order broadcast (BTOB)

4. Which of the properties from Module 6.1 (regular TOB) cannot be achieved with byzantine faulty nodes?

__ANSWER:__ *No Dublication can only be ensured for correct processes. Also, no creation can only be ensured for correct senders.*

5. What can go wrong if we replace reliable broadcast in Algorithm 6.1 with their Byzantine variant 
and use weak-byzantine consensus (Module 5.10, p.245) instead of normal consensus?

__ANSWER:__ *We cannot force a faulty process to propose any specific value. Thus if a faulty process in Alg. 6.1 always proposes the empty set to consensus, this value may be learned an no message will ever be delivered.*

6. How does Algorithm 6.2 avoid the problems you found in e. above?

__ANSWER:__ *Alg 6.2 uses Byzantine consensus with the strong validity property, and ensures that the correct processes all propose the same value, when the leader is correct.*

## Terminating reliable broadcast (TRB)

7. We replace the perfect failure detector in Algorithm 6.3 with an eventually perfect failure detector,
and the `<CRASH>` even with the `<SUSPECT>` event. 
    * Which properties from Module 6.4 still hold? 
    * Can you reformulate the properties that no longer hold?
    
    __ANSWER:__ *With an unreliable failure detector a process may propose the triangle in Alg. 6.3, even if the sender did not crash. Validity may be violated, e.g. a correct sender may broadcast `m`, but if the sender is suspected, the processes may deliver the triangle instead.*
    
    __ANSWER:__  __New Validity:__ *If a correct process `p` broadcasts a message `m` then it eventually delivers `m`, or the triangle. If `p` is never suspected by any other process, then `p` eventually delivers `m`.*
 ## Fast Consensus
 
 8. Give an example of an execution of Algorithm 6.4, where some process decides on the fast path and 
 another process decides on the slow path.

__ANSWER:__ *Assume four processes `p1, p2, p3, p4`. Assume `p1`, `p2`, and `p3` propose `0` and `p4`proposes `1`. 
If a process receives the `<PROPOSAL>` messages from `p1`, `p2`, and `p3` it will decide on `0` on the fast path. 
If a process receives the `<PROPOSAL>` messages from `p4`, among the first 3 proposals, it will propose `0` to consensus, 
and eventually decide on `0` on the slow path.*

## Group membership

9. Consider Algorithm 6.8-6.9. Here the algorithm requests from the application to stop sending messages. 
    * What whould happen if instead, the algorithm would simply stop to forward messages? 
      Which property of Module 6.9 or 6.10 would be violated?
      
    __ANSWER:__ *View Inclusion would be violated. Messages sent in the old view would be delivered first in the new view.*
    
10. If we implement Algorithm 6.10-6.11 in the *fail-noisy* model with an eventually perfect failure detector (<>P) and use 
    the `<SUSPECT>` event instead of `<CRASH>`, what properties from Module 6.10 would still hold?
    * How can we handle the failure bound *f* and the `<RESTORE>` events from <>P?

   __ANSWER:__ *Using an unreliable failure detector, a process may be removed even if it has not crashed. Thus violating Accuracy of Module 6.8. Also messages sent by the removed process may never be delivered. This may violate reliable delivery.*
    
## Good execises from the book
I recommend at least reading all exercises from the book. 
The following ones are especially relevant:

* Exercise 6.8
* Exercise 6.9
* Exercise 6.11
* Exercise 6.13
