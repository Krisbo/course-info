## Definitions

1. What is a *failed* and a *completed* operation?

2. What is a *sequential* execution?

3. Draw a sequence diagram for a sequential execution of a (1,N)-register, 
including 2 write and 2 read operations.

## Regular  vs. atomic

4. Is the execution you have dawn in point 3 regular? Is it atomic?

5. Draw a sequence diagram for an execution of a (1,N)-register 
that is not regular.

6. Draw a sequence diagram for an execution of a (1,N)-register 
that is regular but not atomic.

## Atomic and linearizable

7. The figure below shows an execution of an (N,N)-register.
  * Show that the execution is atomic, by assigning every operation a synchronization point.
  * Show that the execution is linearizable by ordering the operations.

![Figure 1, an execution of an (N,N)-register](fig/CH4-fig1.jpg?raw=true)

8. The two figures below shows an execution of an (N,N)-register with one failed write operation. 
  Remember that failed operations may or may not be included in the order and my pr may not get a synchronization point.
  * Show that the execution is atomic, by assigning every operation a synchronization point.
  * Show that the execution is linearizable by ordering the operations.
  
 ![Figure 2, an execution of an (N,N)-register with a failed write.](fig/CH4-fig2.jpg?raw=true)
 
 ![Figure 3, an execution of an (N,N)-register with a failed write.](fig/CH4-fig3.jpg?raw=true)
