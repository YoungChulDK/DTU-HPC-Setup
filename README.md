# DTU-HPC Setup

This is a simple guide on how to use the HPC and setup your project for simulations on the DTU HPC.

# Getting started

Open the Terminal, and create an SSH connection to the HPC using your student login.

  ssh (Insert student number, sXXXXXX).login.hpc.dtu.dk

Enter your password, and you're connected to the HPC!

**Note:** This only brings you to the login node. This is not a place to run scripts, it is only for entering the HPC!

# Using the HPC 

For interactive usage of the HPC in the Terminal, use one of the interactive nodes. An example of reaching an interactive GPU node is:

  k40sh

This interactive node has a lot of available GPU's which is great for training neural networks. To see the available GPU resources write:

  nvidia-smi
  
TBC..
