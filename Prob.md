# Probability notes from Stat110x course in edX [(link)](https://projects.iq.harvard.edu/stat110)

## Probability, Counting, and Story Proofs

+ **Sample Space** is the set that contains list of all possible outcomes.
+ An event A is said to occur if atleast one of the set's members are the output of some event.
+ <img src="https://render.githubusercontent.com/render/math?math=A \union B"> means either event A or event B occurred. In other words, at least one of A and B occurred.
+ <img src="https://render.githubusercontent.com/render/math?math=A \intersection B"> means both event A and event B occurred. 

### De Morgan's law
<img src="https://render.githubusercontent.com/render/math?math=(A \union B)^c = A^c \intersection B^c"> A or B does not occur is the same as A does not occur and B does not occur. In other words it is not the case that at least one of 𝐴 and 𝐵 occur is the same as saying that 𝐴 does not occur and 𝐵 does not occur.
<img src="https://render.githubusercontent.com/render/math?math=(A \intersection B)^c = A^c \union B^c"> A and B does not occur is the same as A does not occur or B does not occur.

### Naive definition of probability
<img src="https://render.githubusercontent.com/render/math?math=P_(naive) (A) = \frac{number of elements in A}{number of elements in S}">

This definition is naive because it assume that S contains finite number of outcomes and all outcomes have same uniform weight. The definition is still applicable in many cases where there is symmetry in the problem that makes the outcomes equally likely.

### Multiplication Rule

>If event A has `a` possible outcomes and event B has `b` possible outcomes then the compound event has `ab` outcomes, i.e. first event A is performed then event B is performed.

### Sampling with replacement
Consider n objects and choosing k objects from them, one at a time with replacement. Then there are <img src="https://render.githubusercontent.com/render/math?math=n^k"> possible outcomes

### Sampling without replacement
Consider n objects and choosing k objects from them, one at a time without replacement. Then there are <img src="https://render.githubusercontent.com/render/math?math=n(n-1)..(n-k+1)"> possible outcomes


