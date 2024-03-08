---
season: winter
tags: jupyter python snippets
---
When using Python's virtual environment for a project, we want to be able to launch a Jupyter notebooks server from within the virtual environment so that Jupyter can access the environement's installed packages.

1. Activate virtualenv
```
source ./venv/bin/act
```

2. If not done, install ipykernel in `venv`
```
pip install ipykernel
```

3. Install kernel
```
python -m ipykernel install --user --name=myenv
```

4. To remove `myenv`, run
```
jupyter-kernelspec uninstall myenv
```

[source](https://janakiev.com/blog/jupyter-virtual-envs/)
