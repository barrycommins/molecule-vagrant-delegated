Running Molecule on Vagrant Against Itself
=========

If you can't run [Molecule](https://molecule.readthedocs.io/en/latest/) locally, for example on Windows, then it is possible to run it within Vagrant, using the *delegated* driver, and running the molecule tests against the local Vagrant machine.


This project is an example of that. It contains a Vagrantfile that install python, pip, ansible and molecule.

It then runs `molecule test` against the current directory (mounted to the Vagrant machine as /molecule/molecule_vagrant_test, so that molecule can find the role by name, but searching up parent directories until the directory matches the role name).

To run it, just run `vagrant up` from the top level directory.

To test changes, run `vagrant provision --provision-with molecule` which only runs the shell provisioner with the name 'molecule', and doesn't attempt to reinstall python, etc.

The playbook itself is simple, it just installs java. The only test checks if the package has been installed.