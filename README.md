# Virtual Environments
Let's talk about two different Python environment managers: 
- [***conda***](https://conda.io/en/latest/)
- [***venv***](https://virtualenv.pypa.io/en/latest/)
    
You can create virtual environments with either one. Below you'll read about each of these environment managers including some advantages and disadvantages. 

## [conda](https://conda.io/en/latest/) 
Conda does two things: 
- manages packages
- manages environments

As an environment manager, conda allows you to create silo-ed Python installations. With an environment manager, you can install packages on your computer without affecting your main Python installation.

***
### Behaviour 1
If you 
- create a conda environment, 
- activate the environment, and then 
- pip install the distributions package, 

[***packages are globally installed***](https://github.com/ContinuumIO/anaconda-issues/issues/1429) rather than in a local conda environment. 

Basic code
```
conda create --name environmentname
source activate environmentname
conda install numpy
```

***
### Behaviour 2
However, if you 
- create the conda environment and 
- install pip ***simultaneously***, 

***packages are in a local environment installed*** and  pip behaves as expected:

Basic code 
```
conda create --name environmentname pip
```
***

## [pip](https://pypi.org/) and [venv](https://virtualenv.pypa.io/en/latest/)
- venv is an environment manager an comes pre-installed with Python 3. 
- pip is a package manager

Basic code
```
python3 -m venv environmentname
(or: python3 -m virtualenv environmentname)
source environmentname/bin/activate
pip install numpy
```

- `python -m venv venv_name` - a new folder appear with the Python installation named environmentname
- `source venv_name/bin/activate` - environmentname is active
- `pip install python_package/.` That should install your distributions Python package.


### Check which packages are installed 
List all of the Python library that your app depends on
  ```
  pip freeze
  ```

Create a requirements file, which lists all of the Python library that your app depends on
  ```
  pip freeze > requirements.txt
  ```

## Big difference
- Conda manages environments AND packages. 
- Pip only manages packages.
- Conda was invented because pip could not handle data science packages that depended on libraries outside of Python. 
- e.g. NumPy, Matplotlib, etc. are relying on libraries outside of Python.
- Pip venv is better for software application developments