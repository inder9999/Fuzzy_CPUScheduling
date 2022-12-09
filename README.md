# Fuzzy CPU Scheduling

In this Algorithm, Following parameters would be used to calculate the index:
● Burst time is the amount of time that a process wants to execute before it generates an I/O request or terminates 

● CPU usage is the percentage of the amount of time that a process has used CPU 

● A process can increase/decrease its nice value in order to decrease/increase its  priority, respectively

### Basic definitions of Fuzzy Sets and Systems 
● Fuzzy set is defined as a set, in which each member of the set is allowed to have some degree of membership to the set ranging from 0 to 1, unlike the classical set where the  memberships are crisp( either 0 or 1 ) i.e. a member belongs or does not belongs to the  set. The relaxation in crisp nature of the memberships helps to represent the data more  realistically as in real system there is always some degree of uncertainty associated with  the classifications. 

● Fuzzy Inference System: Fuzzy inference is the process of formulating the mapping from a given input to an output using fuzzy logic. Here the mapping is between the fuzzy  sets as input and output. Fuzzy inference systems (FIS) have been successfully applied in  fields such as automatic control, data classification, decision analysis, expert systems, and  computer vision.

### Basic structure of fuzzy inference system 

The first step, fuzzification, takes crisp inputs and determines the degree to which these inputs belong to each of the appropriate fuzzy sets. It is the mapping from universe of discourse to membership value.  

In the second step, the inference engine triggers the appropriate IF-THEN rules in the knowledge base using different  inference methods like Mamdani, Larsen, Tsukamoto,etc.  

Finally, in the third step, the aggregated output fuzzy set is defuzzified to achieve crisp output. Some of the commonly  used defuzzification methods are centroid, weighted average, mean of maximum, center of largest area, maximum  membership

### Basic Structure and Algorithm 
#### Fuzzy decision-making system for CPU scheduler 
The basic structure of proposed fuzzy decision-making system is as follows:

It has three input and one-output. The three inputs are the burst time, nice value and recent CPU usage. The three input parameters are fuzzified and then passed to the fuzzy inference engine comprised of twenty-seven  fuzzy rules. The output of the fuzzy inference engine is later defuzzified to a crisp value which is the dynamic  priority of the processes.

#### Components of proposed Fuzzy Inference System 
● Fuzzifier: This component is responsible for fuzzifying the three input parameters, namely the burst time, nice value, and recent CPU usage of every runnable process. It determines the degree to which  these inputs belong to the three fuzzy sets defined as ‘Low’, ‘Medium’ and ‘High’. These fuzzified inputs  are mapped to the output (dpi) which is represented in terms of five fuzzy sets which are ‘Very_low’,  ‘Low’, ‘Average’, ‘High’, and ‘Very_high’. Triangular membership functions are used for mapping the  crisp input value to a fuzzy membership value between 0 and 1.

● Fuzzy Inference Engine: This component is the actual brain as the logic of our algorithm resides here. The reasoning is applied using IF-THEN type fuzzy rules. These IF-THEN rules formulate the conditional  statements that comprise fuzzy logic. The inference engine triggers the appropriate IF-THEN rules in the  knowledge base using Mamdani–Larsen inference method. There are twenty-seven rules that are used  for fuzzy inference. 

● Defuzzifier: The defuzzifier component takes fuzzy dpi for each process and defuzzifier it to crisp dpi using centroid method.  

### Algorithm
The algorithm for these steps is explained below.  

1. Begin 

2. FIS = create fuzzy inference system  

3. Define linguistic values of input variables; burst time, nice value, and CPU usage.

4. Define linguistic values of output variable: dynamic priority  

5. Read input file and initialize PCB of each process. 

6. Compute recent CPU usage. 

7. Fuzzify the three input parameters. 

8. Trigger fuzzy rule base and compute dpi of each process. 

9. Defuzzify each process’s dpi. 

10. Sort run queue in decreasing order of process dpi. 

11. Select the process at the head of the queue for execution. 

12. If process terminates; remove it from run queue and go to step 11.

13. If time quantum expires or a high-priority process arrives; go to step 6. 

14. End

### Papers
1. P. M. Larsen, “Industrial applications of fuzzy logic control,” International Journal of Man-Machine Studies, vol. 12, no. 1, pp. 3–10, 1980.

2. E. H. Mamdani, “Advances in the linguistic synthesis of fuzzy controllers,” International Journal of Man-Machine Studies, vol. 8, no. 6, pp. 669–678, 1976.

3. Y. Tsukamoto, “An approach to fuzzy reasoning method,”, in Advances in Fuzzy Set Theory and Applications, Edited by M. M. Gupta, R. K. Ragade, and R. R. Yager, Amsterdam: North-Holland, 1979.
