
1. Virtual Environments are created so that specific versions of packages catered to particular app can exist so a same package of different version exist in the same system for different project
2. **VENV**: they are responsible to manage virtual different env
3. ``` bash
   python -m venv projA # this will create a projA directory with python interepretor and different supporting files
   
   # .venv is a common directory name for holding a venv
   
   source projA/bin/activate #1.  start a 
   
			   deactivate # to deactivate a env
   
   python -m pip install package-a #2. to install a package in projA env   
   
   
   ```



## UV
1. Faster alternative of pip build it rust, manages venv, packages, reproduce working environments etc..
2. ```
   uv init
   uv add "package-name"
   
   ```
