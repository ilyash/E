E
=

Maintain CLI environments to work on different projets or clients.

Problem
-------

You have to manage several environments. For example for clients or for different projects. Each project has it's own AWS keys, Chef/Puppet/Your-own-super-cool-tool-here settings, etc. You end up with a bunch of shell scripts that set up such environments. You wish they would be organized better but you never have the time to do that.

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
* `E` - launches `whiptail`-bases menu: 5 most recently used environments at the top `===` separator and then all the environments in alpabetical order.

Screenshots
-----------
(soon)

Advanced configuration
----------------------
(soon)
