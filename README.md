# LEAF 🌱

A simulator for **L**arge **E**nergy-**A**ware **F**og computing environments.
LEAF enables energy consumption modeling of distributed, heterogeneous, and resource-constrained infrastructure that executes complex application graphs.

Features include:

- **Power modeling**: Model the power usage of individual compute nodes, network traffic and applications
- **Energy-aware algorithms**: Implement dynamically adapting task placement strategies, routing policies, and other energy-saving mechanisms
- **Dynamic networks**: Nodes can be mobile and can join or leave the network during the simulation
- **Scalability**: Simulate thousands of devices and applications in magnitudes faster than real time
- **Exporting**: Export power usage characteristics and other results as CSV files for further analysis

<p align="center">
  <img src="/images/infrastructure.png">
</p>


### Implementation

The package `org.leaf` contains the infrastructure and application model as well as related power models.

The current implementation depends on a patched version of CloudSim Plus which can be found [here](https://github.com/birnbaum/cloudsim-plus/pull/1).
Infrastructure and application graphs are implemented through [JGraphT](https://jgrapht.org/).


### Example Scenario
The package `org.examples.smart_city_traffic` implements an exemplary traffic management scenario in a smart city.
The example contains:
- multiple custom compute nodes, network links, and applications
- a mobility model for taxis modelled after a taxi traffic dataset from the  
[2015 DEBS Grand Challenge competition](http://www.debs2015.org/call-grand-challenge.html)
- two different application placement algorithms
- a **live visualization** to monitor experiments at runtime which contains
    - a map of the city and the location of taxis
    - the number of taxis on the map over time
    - the power usage of infrastructure components over time
    - the power usage of applications over time

<img src="/images/visualization.png" width="70%">

Experiments can be configured via the `Settings` class.
To improve simulation speed increase the `LOG_LEVEL` and reduce the `VISUALIZATION_REDRAW_INTERVAL`.


#### Analysis
The directory `analysis` contains the experiment analysis code written in Python.
For running the analysis yourself, [install conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/) adapt `settings.py` and run:

```
cd analysis
conda env create
conda activate leaf_analysis
python create_plots.py
```
