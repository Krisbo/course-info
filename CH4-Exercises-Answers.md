## Definitions

1. What is a *failed* and a *completed* operation?

__Answer__: *A completed operation is an invokation with a matching return. A failed operation is an invoked operation, where the process fails before the operation returns.*

2. What is a *sequential* execution?

__Answer__: *An execution where every two operations are sequential, that meens, one operation returns before another operation is invoked. This includes operations invoked at different processes.*

3. Draw a sequence diagram for a sequential execution of a (1,N)-register, 
including 2 write and 2 read operations.

__Answer__: *Figure 4.3 is a sequential execution. Just add one more read at the end.*

## Regular  vs. atomic

4. Is the execution you have dawn in point 3 regular? Is it atomic?

__Answer__: *Execution in Fig. 4.3 is not regular, therefore not atomic. 
To be regular the read in Fig. 4.3 must return the last value written, `y`*

5. Draw a sequence diagram for an execution of a (1,N)-register 
that is not regular.

__Answer__: *See Fig. 4.3*

6. Draw a sequence diagram for an execution of a (1,N)-register 
that is regular but not atomic.

__Answer__: *See Fig. 4.4 and 4.5*

*Optional:* Think of if the sequence diagram you have drawn is possible for algorithm 4.1 or 4.2 and 
how/why this behaviour is not possible in algorithm 4.5 or 4.6.

__Answer__: *Fig. 4.4 is not possible in Alg. 4.1, Fig 4.5 is possible in Alg. 4.2, Fig 4.6 is possible in 4.2*

## Atomic and linearizable

7. The figure below shows an execution of an (N,N)-register.
  * Show that the execution is atomic, by assigning every operation a synchronization point.
  * Show that the execution is linearizable by ordering the operations.

![Figure 1, an execution of an (N,N)-register](fig/CH4-fig1.jpg?raw=true)

__Answer__: *The order is `W(x), R()-> x, W(y), R() -> y, R() -> y, R() -> y, W(z), R() -> y`*

8. The two figures below shows an execution of an (N,N)-register with one failed write operation. 
  Remember that failed operations may or may not be included in the order and my pr may not get a synchronization point.
  * Show that the execution is atomic, by assigning every operation a synchronization point.
  * Show that the execution is linearizable by ordering the operations.
  
 ![Figure 2, an execution of an (N,N)-register with a failed write.](fig/CH4-fig2.jpg?raw=true)
 
 ![Figure 3, an execution of an (N,N)-register with a failed write.](fig/CH4-fig3.jpg?raw=true)

## Linearizability on a set-object
*difficult exercise*

The point of the following exercise is to see that linearizability or atomicity are meaningfull properties, 
in the context if other distributed objects, than registers.
We therefore look at a set object:

The set has three operations:
 * `add(_)` adds an element to the set
 * `rem(_)` removes an element from the set, if it is part of the set
 * `show()` returns the set, including all elements that have been added but not removed
 
Figure 4 shows a sequential execution of our set. Note that two adds do not result in duplicates.
 
 ![Figure 4, a sequential execution of our set.](fig/CH4-fig4.jpg?raw=true)
 
 
9. The figure below shows an execution of our set. Show that the execution is atomic/linearizable, by assigning synchronization points and ordering operations.

![Figure 5, a concurrent execution of our set.](fig/CH4-fig5b.jpg?raw=true)


*!! There earlier was a mistake in this figure. It is now fixed. The earlier figure (now Figure 6) is not linearizable (atomic). It is still shown below.*

![Figure 6, a concurrent execution of the set object, that is not linearizable.](fig/CH4-fig5.jpg?raw=true)
