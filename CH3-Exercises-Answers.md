## Eager probabilistic broadcast
Eager probabilistic broadcast (Alg 3.9) uses two parameters, *k* and *R*.
Let *P* denote the probability that all processes receive a certain message using eager probabilistic broadcast.
1. What happens with *P* if we increase *R*?
  
  __Answer:__ *If we increase *R*, *P* will also increase towards 1, but not necessarily reach 1.*
  
2. Can you choose *k* and *R* such that *P=1*?
  
  __Answer:__ *We can choose k=N and R=1, then P=1 holds, unless the sender fails.*

## Uniform reliable broadcast
Assume 5 processes are running a uniform reliable broadcast module. If 3 of the processes fail, which of the properties from uniform reliable broadcst (module 3.3) still hold if they are running
* Algorithm 3.4 All-Ack Uniform Reliable Broadcast

__Answer:__*All properties still hold, since the algorithm tolerates N-1 processes failing.*
* Algorithm 3.5 Majority-Ack Unifrom Reliable Broadcast

__Answer:__*URB2 and URB3 (No Creation and No duplication) still hold. They are safety properties.* 
*Uniform agreement and Validity do no longer hold. These are liveness properties.*

* Algorithm 3.4, and the perfect failure detector fails to meet the *strong accuracy* property?

__Answer:__ *Without accuracy, processes can be falsy detected to have failed. Uniform agreement can be violated.*

* Algorithm 3.4 and the perfect failure detector fails to meet the *strong completeness* property?

__Answer:__ *Without completeness, crashed processes may never be detected. All liveness properties (Uniform agreement and validity) can be violated.*

## FIFO and Causal broadcast

1. If we replace the ReliableBroadcast module (*rb*) in algorithm 3.12 with BestEffordBroadcast (*beb*), 
which properties of Module 3.8 (FIFOReliableBroadcast) does the resulting algorithm still implement?

__Answer:__ *FIFO delivery still holds. Validity, No creation and No duplication hold as well, but Agreement does no longer hold.*

2. If we replace the BestEffordBroadcast module *beb* in algorithm 3.3 (Eager Reliable Broadcast) with a FIFOReliableBroadcast (*frb*),
does the resulting algorithm implement *CAUSAL ORDER reliable broadcast*?

__Answer:__ *Yes, the result implements CAUSAL ORDER reliable broadcast.*

## Liveness and Safety

1. Compare the following property to the **causal delivery** property (**CRB5**) of module 3.9:

*If a process delivers messages m1 and m2 and m1->m2 then the process must deliver m1 before m2.*

__Answer:__ *See Solution 3.11 in the book.*

2. Is the above property a liveness or safety property?

__Answer:__ *A safety property. It states that something bad does not happen. If violated, it is violated in a finite prefix of an execution.*
