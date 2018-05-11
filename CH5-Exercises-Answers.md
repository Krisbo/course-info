
## Uniform and regular consensus

* What is the difference between uniform an regular consensus?

__Answer:__ *In uniform consensus, also faulty processes need to agree and cannot output a different value. In regular consensus, a process may decide on one value, then crash and the other processes then decide on a different value.*

* Does uniform consensus implement regular consensus or vice versa?

__Answer:__ *Uniform consensus does implement regular consensus. This means every algorithm for uniform consensus also implements regular consensus.*

* Describe an execution that is possible in regular consensus but not uniform consensus.

__Answer:__ *Process P1 decides `1` and then crashes. Later Process P2 decides `0`.*

---

## Flooding and hierarchical consensus

Assume three processes *p1*, *p2* and *p3* run consensus. *p1* proposes *z*, *p2* proposes *x* and *p3* proposes *y*.
If no processes crash,

* Which value will be chosen by flooding consensus (Alg. 5.1/5.3)?

__Answer:__ *Flooding consensus chooses the minimal value, `min(x,y,z) = x`. Thus `x` will be chosen.*

* Which value will be chosen by hierarchical consensus (Alg. 5.2/5.4)?

__Answer:__ *Hierarchical consensus chooses the value from the process with highest rank. If process `p1` has highest rank, `z` will be chosen.*

---

## Consensus in the fail-noisy model

* Explain why any algorithm, that implements regular consensus in the fail-noisy model must implement uniform consensus.

__Answer:__ *In the fail-noisy model, we only have an unreliable failure detector. Thus the processes cannot distinguish the two cases (1) process `p1` crashes and (2) process `p1` does not crash but is suspected by all other processes. In the second case, regular consensus requires `p1` to decide on the same value as the other processes. Thus the same holds for the first case.*

---

## Randomized consensus

* Why do some algorithms use randomization to solve consensus?

__Answer:__ *It is impossible to solve consensus in the fail-silent model. But using randomization, we can solve consensus without relying on a failure detector (timing assumptions).*

* Does Randomized binary consensus (Alg. 5.12/5.13) 
impement the agreement property from uniform consensus, or only regular agreement?

__Answer:__ *It actually implements uniform consensus. To see this, either study the algorithm in great detail or do a similar argument as above, showing that to implement regular consensus with randomization, we actually need to implement uniform consensus.*

---

## Byzantine consensus

* Compare the weak and strong validity properties of byzantine consensus. Does strong validity implement weak validity?
Can byzantine consensus with weak validity be used to implement strong validity?

__Answer:__ *Strong validity does not implement weak validity and vice versa. But strong validity can be implemented given weak validity. See Solution 5.11 in the book.*

* What triggers a new epoch in Byzantine Leader-Driven Consensus (Alg. 5.19)?

__Answer:__ *All processes maintain a timer. If consensus does not decide within the timeout, the processes complain about the current leader. If `f+1` process complain, a new leader will be elected and a new epoch starts.*

* Compare the Byzantine Read/Write Epoch Consensus (Alg. 5.17, 5.18) to authenticated double-echo broadcast (Alg. 3.18).

__Answer:__ *The `WRITE` and `ACCEPT` messages in Alg.5.18 are similar to the `ECHO` and `READY` messages in Alg. 3.18. The amplification step, where an `READY` message is sent upon receiving f+1 `ECHO` messages is missing from Alg. 5.18, but it could be introduces as an optimization.*

A leader for Byzantine Leader-Driven Consensus receives the following messages in the conditional collect primitive:
```html
m1 = <STATE> ts = 2, v = "X", ws = { (ts = 2, v= "X")}  </STATE>
m2 = <STATE> ts = 1, v = "Y", ws = { (ts = 1, v= "Y")}  </STATE>
m3 = <STATE> ts = 0, v = "Y", ws = { }  </STATE>
```
Assume `N=4`.
* Will the leader wait for another message?

__Answer:__ *Let S be the three `<STATE>`-messages from above. `quorumhighest(2,"X", S)` is true, but `iscertified(2, "X", S)` is not true. Thus `binds(2, "X", S)` is false. `unbound(S)` is also false. Thus the leader needs to wait for more messages.*

Assume the leader receives an additional message:
```html
m4 = <STATE> ts = 0, v = "X", ws = { (ts = 3, v= "Y")}  </STATE>
```
* What value will be written this round?

__Answer:__ *Let `S'={m1, m2, m4}` then `quorumhighest(2,"X", S')` holds and `iscertified(2, "X", S')` holds as well. 
Thus `binds(2, "X", S')` holds and the value "X" will be written.*

---

## Extra execises:

* Compare the three algorithms 5.1, 5.2, 5.3 and 5.4. What are the performance benefits drawbacks?
* What optimizations are possible to Read/Write Epoch Consensus (Alg. 5.6) if it is used inside the Leader driven consensus (Alg 5.7).
* Draw sequence charts for binary probabilistic consensus, one for an execution where the coin is tossed, one for an execution, where the coin has no effect.

