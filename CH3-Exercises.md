## Eager probabilistic broadcast
Eager probabilistic broadcast uses two parameters, *k* and *R*.
Let *P* denote the probability that all processes receive a certain message using eager probabilistic broadcast.
1. What happens with *P* if we increase *R*?
2. Can you choose *k* and *R* such that *P=1*?

## Uniform reliable broadcast
Assume 5 processes are running a uniform reliable broadcast module. If 3 of the processes fail, which of the properties from uniform reliable broadcst (module 3.3) still hold if they are running
* Algorithm 3.4 All-Ack Uniform Reliable Broadcast
* Algorithm 3.5 Majority-Ack Unifrom Reliable Broadcast
* Algorithm 3.4, and the perfect failure detector fails to meet the *strong accuracy* property?
* Algorithm 3.4 and the perfect failure detector fails to meet the *strong completeness* property?

## FIFO and Causal broadcast

1. If we replace the ReliableBroadcast module (*rb*) in algorithm 3.12 with BestEffordBroadcast (*beb*), 
which properties of Module 3.8 (FIFOReliableBroadcast) does the resulting algorithm still implement?

2. If we replace the BestEffordBroadcast module *beb* in algorithm 3.3 (Eager Reliable Broadcast) with a FIFOReliableBroadcast (*frb*),
does the resulting algorithm implement *CAUSAL ORDER reliable broadcast*?

## Liveness and Safety

1. Compare the following property to the **causal delivery** property (**CRB5**) of module 3.9:

*If a process delivers messages m1 and m2 and m1->m2 then the process must m1 before m2.*

2. Is the above property a liveness or safety property?
