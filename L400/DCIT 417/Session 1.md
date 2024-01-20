**Importance of Network Performance Evaluation**
1. Helps select appropriate evaluation techniques, performance metrics, and work-loads for a network system
2. To conduct performance measurement correctly
3. To use proper statistical techniques to compare alternatives
4. To perform simulation correctly
5. To use queuing models to analyse the performance of systems

**Common Mistakes in Performance Evaluation**
1. **Starting without clear goals**: The analyst must understand the system and identify the problem to be solved
2. **Unsystematic Approach**: When analysts arbitrarily select system parameters, factors, metrics and workloads.
3. **Incorrect Performance Metrics**: The analyst should choose metrics that are relevant, rather than ones that can be easily computed or measured.
4. **Unrepresentative Workload**: The choice of workload has a significant impact on the outcome of a performance study. The workload used to compare different systems should be representative of the actual system usage in the field.
5. **Wrong Evaluation Technique**: An analyst should have a basic understanding of all *3*  evaluation techniques and when each one is appropriate to use
`The 3 evaluation techniques are measurement, simulation, and analytical modelling.`

### Systematic Approach to Performance Evaluation
1. **State Goals and Define the System**: The choice of system boundaries affects what metrics and workloads are used to compare the systems
2. **Select metrics**: Select the criteria (metrics) to compare system performance. eg. speed, accuracy, etc
3. **List parameters**: List all parameters that affect system performance. The list can be divided into *system parameters*  and *workload parameters*.
4. **Select factors to study**: The list of parameters can be divided into those that will be varied during the evaluation (*factors*) and those that will not. The values of the factors are called *levels*
### Performance Evaluation Techniques
Deciding which evaluation technique to use is dependent on the *life-cycle stage*  in which the system is.
- Measurement - Something similar to the proposed system already exists
- Analytical modeling and Simulation - Measurement is not possible, new concepts
1. **Analytical Modeling**
Network system > Abstraction > Queuing System Model > Formulation > Graphing/Conclusions

2. **Simulation Modeling**
Network system > Moderate Abstraction > Computer Program > Graphing/Conclusions

3. **Measurement**
Network System > Collect real system data > Measuring device > Graphing/Conclusions

Can measure:
1. Average packet service time
2. Average queue length
3. Probability that waiting time is above a certain threshold

### Comparison of Evaluation Techniques

| **Criterion** | **Analytical Modeling** | **Simulation** | **Measurement** |
| ---- | ---- | ---- | ---- |
| 1. Stage | Any | Any | Post-prototype |
| 2. Time required | Small | Medium | Varies |
| 3. Tools | Analysts | Computer languages | Instrumentation |
| 4. Accuracy | Low | Moderate | Varies |
| 5. Trade-off valuation | Easy | Moderate | Difficult |
|  6. Cost | Small | Medium | High |
| 7. Saleability | Low | Medium | High |
`In general, the results of any evaluation method should not be trusted unless validated by another evaluation method. Hence, it is suggested to use two or more techniques simultaneously`

### Network Performance Metrics
There are **3** kinds of performance metrics
1. *Time-based* metrics: The time b/n two events eg. response time, round trip time
2. *Number-based* metrics: The number of times an event happens or the size of a parameter eg. total number of; packets delivered, errors, failures
3. *Rate-based* metrics: The number of parameter/event count over time eg. packets/sec, jobs/sec
`Metrics that are ratios of two variables have higher variability and should be avoided`
### Commonly Used Performance Metrics
1. **Response time** - Interval b/n user's request and system response
2. **Throughput** - Number of packets delivered per unit time. Increases with increasing system load
`Maximum achievable throughput under ideal workload is called Bandwidth`
3. **Usable capacity** - Maximum throughput achievable w/o exceeding a pre-specified response time limit
4. **Knee** - Optimal operating point. Beyond this point, response time increases rapidly but gain in throughput is small
5. **Knee capacity** - Throughput at knee
6. **Efficiency** - Ratio of maximum achievable throughput (usable capacity) to nominal capacity
7. **Latency** - Time taken to transfer data from source to destination node
8. **Jitter** - Time delay/difference b/n sending each packet over the network.
![[Pasted image 20240120231738.png]]
### Utility Classification of Metrics
- **Higher is Better (HB)** - Higher values are preferred. eg throughput
- **Lower is Better (LB)** - Smaller values are preferred. eg. Latency / Delay
- **Nominal is Best (NB)** - Both low and high values are not preferred. A particular midpoint is best
![[Pasted image 20240120231710.png]]