# How to set up your Python environment

### About
The material in this repo contains information on how to set up your conda and pytorch environment. Follow the same process and create separate environments for conflicting packages, for instance tensorflow.
Also, for reference, the official Laguna website is at: https://uschpc.github.io/regional-computing-website/

### Software Environment Setup
First login to Laguna OnDemand: https://laguna-ood.carc.usc.edu and request a 'Regional Cluster Shell Access' within OpenOnDemand. 

We will use Conda to build software packages. If it is the first time you are using Conda, make sure you follow the guide of how to use Conda with this link: https://www.carc.usc.edu/user-guides/data-science/building-conda-environment

First, we need to request an interactive session:
```bash
salloc --partition=gpu --gres=gpu:1 --cpus-per-task=8 --mem=32GB --time=1:00:00 
```

```
module purge
module load conda
mamba init bash
source ~/.bashrc
module purge
```
```
mamba create --name torch-env python==3.12
mamba activate torch-env
mamba install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```

### Install Jupyter Kernel
Follow the link to CARC Jupyter Kernel documentation: https://www.carc.usc.edu/user-guides/hpc-systems/software/jupyter-kernels and Look for the 'Conda' Section to install Jupyter Kernel. When you finish the installation, type 'exit' to exit from the interactive session.

A Jupyter kernel is a computational engine that executes the code contained in Jupyter notebooks. Each notebook is connected to a specific kernel, which runs the code in the programming language chosen by the user.

For example:

If you’re working in a Python notebook, it will be connected to a Python kernel, allowing Python code execution.
Similarly, Jupyter supports kernels for other languages, such as R, Julia, and MATLAB.

The kernel manages the state of the notebook (such as variables, imports, and output), allowing you to run cells independently while maintaining continuity across the notebook. You can select or switch kernels from within the Jupyter interface.
```
mamba install -c conda-forge ipykernel   # This will install ipykernel inside your Conda environment
python -m ipykernel install --user --name torch-env --display-name "torch-env"     #This will link your Conda environment to OpenonDemand Jupyter Notebook Kernel
exit 
```
```
module load gcc/13.3.0
module load git
```
change your working direcotry to your scratch directory:
```
cd ~
```
```
git clone https://github.com/uschpc/Conda-on-Laguna.git
cd Conda-on-Laguna
```

