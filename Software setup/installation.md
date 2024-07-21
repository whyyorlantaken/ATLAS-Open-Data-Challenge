# Installing ROOT from CERN in Conda for Jupyter Notebook

This document describes how to install Conda, set up a Conda environment for using Jupyter Notebook, and install ROOT for use in Jupyter Notebook.

You can also follow the steps described here: https://iscinumpy.gitlab.io/post/root-conda/
Or here: https://indico.cern.ch/event/759388/contributions/3306849/attachments/1816254/2968550/root_conda_forge.pdf

## Step 0: Install Conda

1. **Download Anaconda**:
   - Visit the official [Anaconda](https://www.anaconda.com/products/distribution#download-section) page.
   - Download the installer suitable for your operating system (Windows, macOS, or Linux).

2. **Install Anaconda**:
   - Follow the installation instructions for your operating system.
   - Make sure to add Anaconda to your PATH if prompted during the installation.

## Step 1: Install Jupyter Notebook

1. **Open Anaconda Prompt or Terminal**:
   - On Windows, search for "Anaconda Prompt" in the Start menu.
   - On macOS or Linux, open a terminal.

2. **Create a basic Conda environment**:
   ```sh
   conda create -n base_env python=3.8

You can change base_env to your preferred name and 3.8 to the Python version you need.

3. **Activate the environment**:
   ```sh
   conda activate base_env
4. **Install Jupyter Notebook**:
    ```sh
   conda install jupyter

## Step 2: Create a Conda Environment with ROOT

1. **Create a new environment with ROOT pre-installed**:
   ```sh
   conda create -n my_root_env root -c conda-forge
   
## Step 3: Activate the Environment with ROOT

1. **Activate the environment**:
   ```sh
   conda activate my_root_env
   
## Step 4: Configure the Conda-forge Channel

1. **Add the conda-forge channel to the environment configuration**:
   ```sh
   conda config --env --add channels conda-forge

## Step 5: Configure the Environment for Jupyter Notebook

1. **Install the Jupyter kernel for the Conda environment**:
   ```sh
   conda install ipykernel
   python -m ipykernel install --user --name=my_root_env --display-name "Python (my_root_env)"

2. **Add the Environment as a Kernel in Jupyter Notebook**:
   ```sh
   python -m ipykernel install --user --name=my_root_env --display-name "Python (my_root_env)"

## Step 6: Run Jupyter Notebook

1. **Start Jupyter Notebook**:
   ```sh
   jupyter notebook

## Step 7: Use ROOT in a Notebook

For more information, you can visit the [ROOT](https://root.cern/) website. 

1. **Create a new notebook**:
   - In Jupyter Notebook, select "New" and choose the Python (my_root_env) kernel you created.

2. **Test ROOT in the notebook**:
   In a notebook cell, try the following code to ensure ROOT is working

   ```python
   import ROOT

   # Crear un histograma simple
   h = ROOT.TH1F("h", "Mi Histograma;Eje X;Eje Y", 100, -4, 4)
   for i in range(10000):
       h.Fill(ROOT.gRandom.Gaus())
   
   # Mostrar el histograma
   c = ROOT.TCanvas()
   h.Draw()
   c.SaveAs("histograma.png")
   
