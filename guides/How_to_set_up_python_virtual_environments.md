# How to set up python virtual environments

## 1. Initial Setup for Ubuntu: _pip_ and _venv_

If you have a Mac, you don't need to do this part.
```console
mig@ubuntu$ sudo apt update && sudo apt upgrade && sudo apt install python3-pip python3-venv
```

## 2. Setup for both Mac and Ubuntu

### 2.1 Install _pip_

_pip_ is the reference Python package manager. It’s used to install and update packages. You’ll need to make sure you have the latest version of pip installed.

To install _pip_, type the following on your terminal:
```console
mig@MacBook-Pro$ python3 -m pip install --user --upgrade pip setuptools wheel
```

Afterwards, you should have the newest pip installed:
```console
mig@MacBook-Pro$ python3 -m pip --version
pip 22.0.2 from /Users/mig/Library/Python/3.10/lib/python/site-packages/pip (python 3.10)
```

### 2.2 Set up a virtual environment

_venv_ is a Python Standard Library module that allows us to create isolated Python environments (called virtual environments).  We'll use it to keep an isolated Python environment where we will install the specific Python packages we use in the specializations.
You should always use a virtual environment to install Python packages (such as jupyter notebook, pandas, numpy, etc) and should never install packages outside of a virtual environment. This is because Linux based Operating Systems (OS) use Python as a part of their system, and installing Python packages onto the OS's Python may leave the OS in an inconsistent state.   

We'll be storing all our virtual environments in the `~/.virtualenvs` folder.  
The following command will create a virtual environment called `s01`, which will be stored inside the `~/.virtualenvs/`.  
To create a virtual environment called `s01` (you may use whatever name you like), type:
```console
mig@MacBook-Pro$ python3 -m venv ~/.virtualenvs/s01
```

We will now activate our virtual environment by typing the command below.
Notice that once we do, the name of our virtual environment appears in parenthesis at the left side of the command line.
  
```console
mig@MacBook-Pro$ source ~/.virtualenvs/s01/bin/activate
(s01) mig@MacBook-Pro$
```

By using the `which` command, we can see that inside the virtual environment, we are using a different Python installation, and are now safe to start installing Python packages to it.

```console
mig@MacBook-Pro$ which python3
/usr/bin/python3
mig@MacBook-Pro$ source ~/.virtualenvs/s01/bin/activate
(s01) mig@MacBook-Pro$ which python
source ~/.virtualenvs/s01/bin/activate/
/Users/mig/.virtualenvs/s01/bin/python
```

First we will upgrade our virtual environment's version of pip:
```bash
pip install -U pip
```

Notice that because we used the default python3 to create our virtual environment, when we have the virtual environment active, we can refer to python3 as just python, and to pip3 as just pip.

We can also deactivate our virtual environment (note that deactivating a virtual environment **does not** remove it) by typing the command below.  
By doing this, we stop working in our isolated Python environment.
Notice that once we leave the virtual environment, the name of our virtual environment disappears from the left side of the command line:
```console
(prep-venv) mig@MacBook-Pro$ deactivate
mig@MacBook-Pro$
```

You can see all your virtual environments by listing the directories in the `~/.virtualenvs` directory:
```console
(s01) mig@MacBook-Pro$ ls ~/.virtualenvs
s01
```

To remove a virtual environment, we need to deactivate it and remove the folder where it's stored. You might need to remove a virtual environment after you no longer need it or if it breaks:
```console
(s01) mig@MacBook-Pro$ deactivate
mig@MacBook-Pro$ rm -r ~/.virtualenvs/s01
```

### 2.3 Installing Python packages using _pip_

For installing Python packages, make sure to have your virtual environment active:
```console
mig@MacBook-Pro$ source ~/.virtualenvs/s01/bin/activate
(s01) mig@MacBook-Pro$ 
```

To install one package, simply type `pip install` followed by the name of the package:
```console
(s01) mig@MacBook-Pro$ pip install numpy
```

To install multiple packages in one go, type `pip install` followed by the names of the packages separated by a single space:
```console
(s01) mig@MacBook-Pro$ pip install matplotib pandas
```

In each specialization you will be provided with a `requirements.txt` file that contains a list with all the Python packages you need for this specialization. 
To install packages from a `requirements.txt` file:
```console
(s01) mig@MacBook-Pro$ pip install -r requirements.txt
```

## References
* https://realpython.com/python-virtual-environments-a-primer/
* https://packaging.python.org/guides/installing-using-linux-tools/
* https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/
* https://docs.python.org/3/library/venv.html
* https://packaging.python.org/tutorials/installing-packages/#id12
