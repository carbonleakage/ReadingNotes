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
<img src="https://render.githubusercontent.com/render/math?math=P_{naive} (A) = \frac{|A|}{|S|}">

This definition is naive because it assume that S contains finite number of outcomes and all outcomes have same uniform weight. The definition is still applicable in many cases where there is symmetry in the problem that makes the outcomes equally likely.

### Multiplication Rule

If event A has `a` possible outcomes and event B has `b` possible outcomes then the compound event has `ab` outcomes, i.e. first event A is performed then event B is performed.

### Sampling with replacement
Consider n objects and choosing k objects from them, one at a time with replacement. Then there are <img src="https://render.githubusercontent.com/render/math?math=n^k"> possible outcomes

### Sampling without replacement
Consider n objects and choosing k objects from them, one at a time without replacement. Then there are <img src="https://render.githubusercontent.com/render/math?math=n(n-1)..(n-k+1)"> possible outcomes

### Binomial coefficient
If there are n objects of which k objects are chosen at a time then there are <img src="https://render.githubusercontent.com/render/math?math{n\choose k}=\frac{n!}{(n-k)!k!}">

### General definition of probability

A probability space consists of a sample space 𝑆 and a probability function 𝑃 which takes an event <img src="https://render.githubusercontent.com/render/math?mathA \subset S"> as input and returns 𝑃(𝐴), a real number between 0 and 1, as output. The function 𝑃 must satisfy the following axioms:

+ <img src="https://render.githubusercontent.com/render/math?mathP(\null) = 0, P(S) = 1">
+ If <img src="https://render.githubusercontent.com/render/math?mathA_1, A_2..."> are disjoint events (saying that these events are disjoint means that they are mutually exclusive: 𝐴𝑖∩𝐴𝑗=∅ for 𝑖≠𝑗., then <img src="https://render.githubusercontent.com/render/math?mathP(A_1 \union A_2 ...) =  \sum{j=1}{\infinity} P(A_j)">