# DTU HPC for Python Project Setup

This is a simple guide on how to use the HPC and setup your project for simulations on the DTU HPC.

# Getting started

Open the Terminal, and create an SSH connection to the HPC using your student login. This is an example using my student number as login.
```
ssh s134550.login.hpc.dtu.dk
```
Enter your password, and you're connected to the HPC!

**Note:** This only brings you to the login node. This is not a place to run scripts, it is only for entering the HPC!

# Using the HPC Nodes

For interactive usage of the HPC in the Terminal, use one of the interactive nodes. An example of reaching an interactive GPU node is:
```
k40sh
```
This interactive node has a lot of available GPU's which is great for training neural networks. To see the available GPU resources write:
```
nvidia-smi
```
# Loading Pre-Installed HPC Modules

The HPC has a lot of pre-installed modules available, the modules can be listed by using the command
```
module avail
```
To load a module, simply write
```
module load (module name)
```
In case of a conflict, or if you need to use an alternative module, you can also unload the modules by writing
```
module unload (module name)
```

# Setting up your project environment and installing modules

As you have limited writing access on the HPC, and you are not allowed to install additional modules directly onto the HPC, it is useful to setup a virtual environment for your project.

This also allows you to install Python site-packages which are not included in the pre-installed modules such as Keras, newer versions of OpenCV, Tensorflow etc.

In Python 3, you can create a Python 3 virutal environment easily, without the usage of virtualenv. This is simply done by stating

```
python3 -m venv (Name of virutal environemnt)
```
To activate your virtual envirnment do
```
source ~/(Name of virtual environemnt)/bin/activate
```

Now you are allowed to install packages within this virtual environemnt using Pip3 or similar, however do not use SUDO commands as it will get reported to the admins.

**Note:** If Pip3 gives you a writing permission error, it might be because you are "looking outside" of the virtual environment. To make sure you are using the pip installation from within your virtual env. use the command

```
which pip3
```
Which shows you the path to the installation.

Now you can install most of the common Python packages easily and pain free.
