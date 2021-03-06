# DTU HPC Setup for Python 3 Projects

This is a simple guide on how to use the HPC and setup your Python projects on the DTU HPC.

Please read to the official guide on proper usage of the HPC first: https://www.hpc.dtu.dk/

# Getting started - File transfer

To transfer your files to DTU G-Bar, you can either use SSH or a simple file transfer program like FileZilla.

Do not use the login nodes to transfer big files, use the dedicated transfer server. 

**Transfer files using FileZilla**

Use Quickconnect (Top bar) and enter the following.

**Host:** transfer.gbar.dtu.dk, **Username:** sXXXXXX (Your DTU Student ID), **Password:** (Your DTU password), **Port:** (Any, example: 22)

It will direct you to your personal part of the drive, create a new folder here to start a project.

**Transfer files using SSH**

Please read the following guide:

http://gbar.dtu.dk/faq/53-ssh

# Logging in to the HPC

Open the Terminal on your computer, and create an SSH connection to the HPC using your student login.
```
ssh sXXXXXX@login2.hpc.dtu.dk
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
As the resources are shared, make sure to pick one that is not too busy. This can be done by explicitly writing
```
CUDA_VISIBLE_DEVICES= (PICK GPU #, Check available ones using 'nvidia-smi'!)
```
Before you run your script. Like:
```
CUDA_VISIBLE_DEVICES=3 Python example.py
```
This will execute the Python script 'example.py' using the GPU Device 3. (Remember they are 0 indexed)

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
or
```
module swap (module name)
```

# Setting up your Python project environment and installing modules

As you have limited writing access on the HPC, and you are not allowed to install additional modules directly onto the HPC, it is useful to setup a virtual environment for your project.

This also allows you to install Python site-packages which are not included in the pre-installed modules such as Keras, newer versions of OpenCV, Tensorflow etc.

**Python 3**

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

**Python 2.7**

Visit https://virtualenv.pypa.io/en/stable/ for more information about setting up a Virtual Environment for Python 2.7 projects.

-----------
Now you can install most of the common Python packages easily and pain free.

# Example

In this repository, I have attached a quick and simple bash script, to install the Keras packages for Python 3.6.2 using a Tensorflow (GPU compiled) backend, in a virtual environment called 'hello_tensorflow'.

Remember to login before using this script, then run it by writing 

```
sh hpc_keras_quick_setup_example.sh
```

Then open Python and check if the package is installed correctly.

```
Python3
>>import keras
>>exit()
```
