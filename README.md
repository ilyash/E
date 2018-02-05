E
=

Maintain CLI environments to work on different projets or clients.

Problem
-------

You have to manage several environments (where environment is a set of environment variables). For example for clients or for different projects. Each project has it's own AWS keys, Chef/Puppet/Your-own-super-cool-tool-here settings, etc. You end up with a bunch of shell scripts that set up such environments. You wish they would be organized better but you never have the time to do that.

Suggested solution
------------------
E provides lightweight framework in bash allowing some order and organization of such scripts. E also makes it easy to move the common parts of such scripts to one place, allowing better maintenance.

Setup
-----
* Place the E binary somewhere in the path.
* Create the ~/.E directory.

Adding new environment
----------------------
* Create a directory, named after the project name.
* `cd` to that directory
* Create `.env.sh` file (empty or with bunch of `export X=Y` lines or more advanced stuff)
* Run `E add`

Activating an environment
-------------------------
Alternatives
* `E <env-name>` - activates the given environment
* `E` - launches `whiptail`-based menu: 5 most recently used environments at the top `===` separator and then all the environments in alpabetical order.

Setup and work toaster
----------------------
```
# E binary setup - start
cd
grep -qF ":$HOME/.bin" ~/.bashrc || echo "export PATH=$PATH:$HOME/.bin" >>~/.bashrc
mkdir .bin
wget -O .bin/E https://raw.github.com/ilyash/E/master/E
. ~/.bashrc
chmod +x .bin/E
mkdir .E
# E binary setup - done

# Setting up "my-super-proj" project - start
mkdir my-super-proj
cd my-super-proj
echo "export TEST=1" >.env.sh
E add
# ignore the error "grep: ..../.E/list: No such file or directory"
# Setting up "my-super-proj" project - done

# Work with an environment - start
E
# pick the project in the menu
# output: *** Setting up environment 'my-super-proj' ***
# when finished: CTRL+D
# output: *** Exited environment 'my-super-proj' ***
# Work with an environment - done
```

Suggested bashrc additions
--------------------------
```
if [ -f ~/.bin/E.completion ]; then
  . ~/.bin/E.completion
fi

alias cdd='cd $E_HOME'
```

Screenshots
-----------
![screenshot of "E" running without arguments](img/screenshot-select.png "screenshot of \"E\" running without arguments")

Advanced configuration
----------------------
(soon)
