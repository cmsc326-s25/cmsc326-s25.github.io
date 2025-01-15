# Setting Up Your Conda Environment for SimulationS25

This guide will help you set up a Conda environment with everything you need to run Jupyter Notebooks for the Simulation course. The environment includes essential libraries like Matplotlib, and NumPy.

## Prerequisites

1. Install [Anaconda](https://www.anaconda.com/download).
 
 
## Steps to Set Up the Environment

1. **Download the Environment File**

Save the following YAML file as `environment.yml` on your computer:

   * Download link here: [environment.yml](https://raw.githubusercontent.com/cmsc326-s25/cmsc326-s25.github.io/refs/heads/main/files/install/environment.yml)

```yaml
name: simulationS25
channels:
    - conda-forge
dependencies:
    - python=3.11
    - colour>=0.1.5
    - jpype1>=1.4
    - jupyterlab
    - line_profiler>=4.0
    - matplotlib>=3.7
    - numpy>=1.24
    - pandas>=1.5
    - pint>=0.22
    - pillow>=9.5
    - pip
    - pylab
    - scipy>=1.10
    - shapely>=2.0
    - trimesh>=3.23
    - pip:
        - py5[jupyter]
```

2. **Create the Environment**

Open a terminal or command prompt, navigate to the folder where you saved `environment.yml`, and run:

```bash
conda env create -f environment.yml
```


3. **Activate the Environment**

After the environment is created, activate it with:

```bash
conda activate simulationS25
```


4. **Launch JupyterLab**

Start JupyterLab to test the environment:

```bash
jupyter lab
```


5. **Verify the Setup**

Create a new notebook and run the following code to verify the required libraries are installed:

```python
import matplotlib
import numpy
import pandas
import pint

print("Matplotlib version:", matplotlib.__version__)
print("NumPy version:", numpy.__version__)
print("Pandas version:", pandas.__version__)
print("Pint version:", pint.__version__)
```
 

Then run this code in a different Python cell to verify that the py5 graphics work. 

```python
import py5

def setup():
    py5.size(300, 300)

def draw():
    py5.fill(255) 
    py5.ellipse(py5.width / 2, py5.height / 2, 200, 200)
    py5.fill(0)  
    py5.ellipse(py5.width / 2 - 50, py5.height / 2 - 40, 20, 20)
    py5.ellipse(py5.width / 2 + 50, py5.height / 2 - 40, 20, 20)
    py5.arc(py5.width / 2, py5.height / 2 + 20, 100, 60, 0, py5.PI)
    py5.text_size(50)
    py5.text("It Works!", 60, 40)

py5.run_sketch()
```