# Eagle Delivery

Eagle Delivery is a Python project that simulates a campus delivery robot. It uses BFS and A* to find shortest routes and Q-learning to learn routes through experience. A custom campus map is used to study how exploration (epsilon) affects learning.

## Requirements

Python 3.9 or newer. From the GitHub repository's main folder, run:

```powershell
cd starter
```

The commands below use the Windows `py` launcher (`python3` also works on systems that support it).

## Run and test

```powershell
py run_project.py show
py -m unittest discover -v
py run_project.py search --algorithm bfs --start S --goal W
py run_project.py search --algorithm astar --start S --goal W
py run_project.py search --map maps/my_campus.txt --algorithm astar --start S --goal W
```

## Experiments

Baseline Q-learning tasks:

```powershell
py run_project.py train --start S --goal W --output results/baseline_SW
py run_project.py train --start L --goal D --output results/baseline_LD
py run_project.py train --start H --goal P --output results/baseline_HP
```

Custom-map exploration experiment (S to W):

```powershell
py run_project.py train --map maps/my_campus.txt --epsilon 0.05 --output results/custom_e005
py run_project.py train --map maps/my_campus.txt --epsilon 0.2 --output results/custom_e020
py run_project.py train --map maps/my_campus.txt --epsilon 0.5 --output results/custom_e050
```

All runs use **2,000 training episodes per seed**, seeds **0, 1, 2**, **100 evaluation episodes**, **200 maximum steps**, **alpha = 0.3**, **gamma = 0.95**, and **slip = 0.0**. Baseline epsilon is **0.2**.

Results are saved as CSV files in each `results/` subfolder. For example, summarize an experiment with:

```powershell
py summarize_results.py results/custom_e005
```
