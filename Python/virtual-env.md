# Cultivating Virtual Environments

In the Python world, a virtual environment is a folder containing packages and other dependencies that a Python project needs. 

Contrary to a global environment, virtual environments are isolated coding spaces where Python packages can be installed, upgraded, and used. When you install or upgrade a package, the old versions stay installed in your directory, so different virtual environments can utilize different package versions. 

## Managing My Virtual Environment
 - create virtual environment
 - exclude virtual environment from the project code
 - activate virtual environment
 - create a list of depdendencies
 - deactivate virtual environment

```console
~/ $ python3 -m venv app1/envs
~/ $ cd app1
~/app1/ $ git init
~/app1/ $ echo envs > .gitignore  
~/app1/ $ source envs/bin/activate
~/app1/ $ pip3 install django 
~/app1/ $ pip3 freeze > requirements.txt  
~/app1/ $ git add requirements.txt
~/app1/ $ deactivate
```
  
