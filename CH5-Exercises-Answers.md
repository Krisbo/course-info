
## Uniform and regular consensus

* What is the difference between uniform an regular consensus?
* Does uniform consensus implement regular consensus or vice versa?
* Describe an execution that is possible in regular consensus but not uniform consensus.

---

## Flooding and hierarchical consensus

Assume three processes *p1*, *p2* and *p3* run consensus. *p1* proposes *z*, *p2* proposes *x* and *p3* proposes *y*.
If no processes crash,

* Which value will be chosen by flooding consensus (Alg. 5.1/5.3)?
* Which value will be chosen by hierarchical consensus (Alg. 5.2/5.4)?

---

## Consensus in the fail-noisy model

* Explain why any algorithm, that implements regular consensus in the fail-noisy model must implement uniform consensus.

---

## Randomized consensus

* Why do some algorithms use randomization to solve consensus?

* Does Randomized binary consensus (Alg. 5.12/5.13) 
impement the agreement property from uniform consensus, or only regular agreement?

---

## Byzantine consensus

* Compare the weak and strong validity properties of byzantine consensus. Does strong validity implement weak validity?
Can byzantine consensus with weak validity be used to implement strong validity?
* What triggers a new epoch in Byzantine Leader-Driven Consensus (Alg. 5.19)?
* Compare the Byzantine Read/Write Epoch Consensus (Alg. 5.17, 5.18) to authenticated double-echo broadcast (Alg. 3.18).

A leader for Byzantine Leader-Driven Consensus receives the following messages in the conditional collect primitive:
```html
m1 = <STATE> ts = 2, v = "X", ws = { (ts = 2, v= "X")}  </STATE>
m2 = <STATE> ts = 1, v = "Y", ws = { (ts = 1, v= "Y")}  </STATE>
m3 = <STATE> ts = 0, v = "Y", ws = { }  </STATE>
```
Assume `N=4`.
* Will the leader wait for another message?

Assume the leader receives an additional message:
```html
m4 = <STATE> ts = 0, v = "X", ws = { (ts = 3, v= "Y")}  </STATE>
```
* What value will be written this round?

---

## Extra execises:

* Compare the three algorithms 5.1, 5.2, 5.3 and 5.4. What are the performance benefits drawbacks?
* What optimizations are possible to Read/Write Epoch Consensus (Alg. 5.6) if it is used inside the Leader driven consensus (Alg 5.7).
* Draw sequence charts for binary probabilistic consensus, one for an execution where the coin is tossed, one for an execution, where the coin has no effect.

