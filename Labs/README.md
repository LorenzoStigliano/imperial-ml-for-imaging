# Machine Learning for Imaging - Lab Tutorials

## Getting started

For the lab tutorials, we are making use of [Jupyter Notebook](http://jupyter.org/), a web application that allows you to run code directly in a web browser. For each tutorial, we provide a notebook file with example code and coding exercises. Here, we are explaining three different ways of doing the lab tutorials.

## Option 1: Google Colab

This is the easiest option. You can directly run the provided notebooks on Google Colab with free access to GPUs. You can start Google Colab here: https://colab.research.google.com

## Option 2: Setup a local Python environment on your own machine

### Step 1a: Using conda

Create and activate a Python3 conda environment (we recommend installing miniconda):

   ```shell
   conda create -n mli python=3.10
   conda activate mli
   ```

Install PyTorch using conda:

   ```shell
   conda install pytorch torchvision cpuonly -c pytorch
   ```

The above is for the CPU-only version.

Please see the [PyTorch website](https://pytorch.org/get-started/locally/) for more details and different options for installing PyTorch.

### Step 1b: Using virtualenv

Create and activate a Python3 virtual environment:

   ```shell
   virtualenv -p python3.10 <path_to_env>/mli
   source <path_to_env>/mli/bin/activate
   ```

Install PyTorch using pip:

   ```shell
   pip install torch torchvision
   ```

Please see the [PyTorch website](https://pytorch.org/get-started/locally/) for more details and different options for installing PyTorch.

### Step 2: Install additional Python packages

Whether you used conda or virtualenv, you can install all additional packages using pip:

   ```shell
   pip install matplotlib jupyter pandas seaborn scikit-learn imageio attrdict tqdm vtk SimpleITK
   ```

### Step 3: Running Jupyter notebook

Make sure your Python environment is activated. [Download (or clone) the Jupyter notebooks](https://gitlab.doc.ic.ac.uk/bglocker/mli-tutorials) and run the following command from the same folder that contains the notebook files:

   ```shell
   jupyter notebook
   ```

## Option 3: Remote use of lab machines with pre-configured Python

We provide a pre-configured [virtualenv](https://virtualenv.pypa.io/) Python environment which contains all required dependencies and packages. For this option, you will need to be connected to the [College VPN](https://www.imperial.ac.uk/admin-services/ict/self-service/connect-communicate/remote-access/virtual-private-network-vpn/).

Use ssh to log into one of the lab machines (see this [list of available workstations](https://www.imperial.ac.uk/computing/csg/facilities/lab/workstations/)).

   ```shell
   ssh <machine_name>.doc.ic.ac.uk  
   ```

The Python environment can be activated by running the following command.

On tcsh shell:

   ```shell
   source /vol/lab/course/416/venv/bin/activate.csh
   ```

On bash shell:

   ```shell
   source /vol/lab/course/416/venv/bin/activate
   ```

[Download (or clone) the Jupyter notebooks](https://gitlab.doc.ic.ac.uk/bglocker/mli-tutorials) to your DoC home directory (or any sub-folder) and run the following command from the same folder that contains the notebook files:

   ```shell
   jupyter notebook --no-browser --port=8888
   ```

Copy the generated token (48-character string) from the command line output. Open a new terminal on your computer and connect to the remote lab machine with:

   ```shell
   ssh -N -f -L localhost:8888:localhost:8888 <machine_name>.doc.ic.ac.uk  
   ```

Use any web browser to open the page http://localhost:8888/tree. Paste the copied token for authentication and the Jupyter notebook application should open.

Note, you may have to use different ports if 8888 is already in use on your own or the lab machine.
