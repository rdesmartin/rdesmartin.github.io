---
season: winter
tags: jupyter python snippets
---

Launch Jupyter notebooks server from within a Python virtual environment so that it can access the environement's installed packages.

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
