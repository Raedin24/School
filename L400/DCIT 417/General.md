- Network performance analysis might be done to compare the performances of different protocols on a network.
- It might also be done to see how a prototype of a network might work

Performance can be measured through
1. Mathematical model
2. Computational simulations
3. Experiments
4. Test beds - Where the experiments are done on a small scale with only a few devices. Usually done right after simulation.
`Mathematical modelling is the furthermost from reality because there is a lot of abstraction involved in the calculation, as the model cannot account for all the variables that would be present in the real world`

## Need for Simulation
1. Complexity - huge networks
2. Cost - space communication, satellite
3. Dangerous - PPDR systems, emergency networks (cannot be done in production)

An event is when a packet is generated, dropped to another layer etc. Event can trigger and be triggered by other events.  Most simulations are discrete-event simulations.
## Quick alternatives evaluation
1. Star/mesh topology
2. TCP / UDP
### Pros:
1. Cheaper (compared to production environments and experimentation)
2. Bugs can be found in advance
3. Generality
4. Detail - The granularity of the system can be tuned in detail
### Cons:
1. Accuracy - Does the simulation reflect reality? Usually approximates reality instead of reflecting it accurately.
2. Large scale system - Lots of resources needed for simulation
3. May be slow - As a result of lack of computational power.