# DGAA*: Dynamically Repaired Double-Strand Break Genetic Algorithm with Pheromone Guided A*

## Overview

DGAA* is a novel hybrid path-planning algorithm designed for autonomous quadrupedal robots, combining the strengths of three established algorithms:
- **A-star (A*)** - Efficient heuristic pathfinding
- **Ant Colony Optimization (ACO)** - Global exploration with pheromone guidance
- **Genetic Algorithm (GA)** - Evolutionary path optimization

The algorithm is inspired by biological DNA repair mechanisms and meiotic crossover processes to create robust, efficient paths in both static and dynamic environments.

## Key Features

- **Hybrid Approach**: Leverages the best aspects of A*, ACO, and GA while mitigating their individual limitations
- **Bio-Inspired Mechanisms**: Implements Double-Strand Break (DSB) crossover and Break-Induced Repair (BIR) mutation strategies
- **Adaptive Exploration**: Dynamically balances exploration and exploitation based on target discovery and environment complexity
- **Multi-Threaded Support**: Available in both single-threaded and multi-threaded versions for performance optimization
- **Pheromone-Guided Pathfinding**: Uses modified A* heuristics influenced by pheromone trails

## Target Applications

- Agricultural automation
- Search and rescue operations
- Security and surveillance
- Hazardous environment exploration
- Swarm robotics
- Guide dog robotics

## Hardware Platform

Primary implementation target: **Unitree Go1 Quadrupedal Robot**

### Supporting Technology Stack
- **Vision**: Spectral HD webcam, YOLO object detection, Canny Edge Detection, MiDas Depth Estimation
- **Motion Tracking**: OptiTrack Flex 3 motion capture cameras with IR nodes
- **Navigation**: LiDAR and native cameras for 2D environment mapping

## Algorithm Components

### 1. Population and Generation Sizing
- Ant base calculation: `log₂(m) - 1` (where m = map dimensions)
- Generation size: `⌊((a-1)/2 * 100) - 100⌋`
- Population size: `a * 2 - 2`

### 2. Modified A* Heuristic
```
h(n) = [c + u] * d
```
Where:
- `c` = confidence (target ratio × traditional h(n))
- `u` = uncertainty factor
- `d` = pheromone displeasure

### 3. Selection Strategy
- Preserves top 10% of paths for next generation
- Minimum of 2 chromosomes required for selection

### 4. Crossover Mechanism
- Bio-inspired Double-Strand Breaks (DSBs)
- Implements crossover interference using beam-film model
- Mimics centromere effect to prevent detrimental breaks
- Switches between Class 1 and Class 2 crossover types based on path performance

### 5. Mutation Process
- Break-Induced Repair (BIR) approach
- Random DSB placement with target shuffling
- Introduces path variation for optimization

## Performance Comparison

The algorithm has been tested against:
- Standard A*
- Pure Genetic Algorithm (GA)
- Ant Colony Optimization (ACO) - threaded and non-threaded
- DGAA* - threaded and non-threaded

Results show promising improvements in navigation efficiency across various map configurations.

## Future Development

### Planned Enhancements
1. **Error Detection and Patching (EDP)** system for gait sequencing optimization
2. **Multi-robot coordination** with priority-based conflict resolution
3. **Anchor point system** for collaborative robotics
4. **UAV integration** for guiding ground robots (e.g., Husky A300)
5. Complete automation of Unitree Go1 Dog platform

## Research Team

**Kennesaw State University**
- J. Ridley (Computer Science)
- M.H. Tanveer (Robotics and Mechatronics Engineering)
- RC. Voicu (Robotics and Mechatronics Engineering)
- A. Charles (Robotics and Mechatronics Engineering)
- R. Ahmed (Robotics and Mechatronics Engineering)
- O. Irfan (Robotics and Mechatronics Engineering)

## Status

⚠️ **Current Phase**: Algorithm simulation and validation
- Base DGAA* algorithm under refinement
- Hardware integration pending
- EDP mechanism in development

## Citation

If you use this algorithm in your research, please cite:

```
Ridley, J., Tanveer, M.H., Voicu, R.C., Charles, A., Ahmed, R., & Irfan, O.
DGAA*: A Dynamically Repaired Double-Strand Break Genetic Algorithm with 
Pheromone Guided A*. Kennesaw State University, 2025.
```

## License

Please contact the research team for licensing information.

## Contact

Department of Robotics and Mechatronics Engineering  
Department of Computer Science  
Kennesaw State University  
Marietta, GA 30060, USA
