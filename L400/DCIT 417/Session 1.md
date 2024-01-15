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
**Analytical Modeling**
Network system > Abstraction > Queuing System Model > Formulation > Graphing/Conclusions

**Simulation Modeling**
Network system > Moderate Abstraction > Computer Program > Graphing/Conclusions

**Measurement**
Network System > Collect real system data > Measuring device > Graphing/Conclusions

