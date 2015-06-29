# taskbuster
First Python Project: http://www.marinamele.com/taskbuster-django-tutorial

pip3
python3
django 1.8
selenium

## Environment Mangemment
### pyvenv
Create a new virtual environment
```
$> cd taskbuster/env
$> pyvenv myenv
[creates myenv virtual environment directory]
$> source taskbuster/env/myenv/bin/activate
[activates myenv virutal environment]
$> deactivate
```

Add a dependency to a virutal environment
```
$> source taskbuster/env/taskbuster_test/bin/activate
$> pip install mypackage
$> pip freeze
[shows installed packages]
$> deactivate
```

### virtualenv
Create directory for virutal environments
```
$> mkdir ~/.pyvirtualenvs
```

Install virutalenv and virtualenvwrapper
```
$> pip3 install virtualenv virtualenvwrapper
```

Add the following to .bash_profile
```
export WORKON_HOME=$HOME/.pyvirtualenvs
export PROJECT_HOME=$HOME/Development/git
export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3
source /usr/local/bin/virtualenvwrapper.sh
```

Create a requriements directory and file per environment 
```
$> mkdir requriements
$> touch requriements/{base.txt,env1.txt,env2.txt}
```

Make each env inherit from base
```
$> echo "-r base.txt" | tee -a env1.txt env2.txt
```

Specify shared dependencies in base.txt, and and environment specific dependencies in the appropriate env file.
```
$> echo "sharedDependency==1.0" >> requriements/base.txt
$> echo "env1Dependency==1.0" >> requriements/env1.txt
```

Init environment & dependencies for the first time
```
mkvirtualenv env1
pip install -r requriements/env1.txt
```

Load & unload an environment
```
workon env1
workon env2
deactivate
```



## Run tests
```
$> source taskbuster/env/taskbuster_test/bin/activate
$> python manage.py runserver
[check localhost:8000]
$> python functional_tests/all_users.py
[tests should pass]
$> deactivate
```

###