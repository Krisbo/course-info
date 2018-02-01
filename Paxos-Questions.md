1. What causes the Paxos algorithm to advance to a higher round?
2. Draw a sequence diagram for a Paxos execution, with message loss, including 3 rounds, 
where no value is learned/decided in the first two rounds.
3. Draw a sequence diagram for a Paxos execution, with message loss, including 3 rounds, 
where a value is learned/decided in the second round.
4. What happens in Paxos if multiple proposers use the same round?
5. Assume three replicas are running the Paxos algorithm. Assume at some point in the execution
the three acceptors A1, A2 and A3 have the following state
  ```
  A1: rnd = 3, vrnd = 1, vval = "Hello World"
  A2: rnd = 2, vrnd = 2, vval = "Hei You"
  A3: rnd = 3, vrnd = 3, vval = "Hello World"  
  ```
  * Can the value "Hei Norge" be learned in round 4?
  * Can the value "Hello World" be learned in round 4?
  * Can you draw a sequence diagram for an execution that results in this state?
