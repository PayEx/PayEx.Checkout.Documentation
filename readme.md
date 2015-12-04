# Payex Checkout Documentation

![read the docs build](https://readthedocs.org/projects/payex-checkout/badge/?version=latest)
## Source for [the documentation hosted on Read the Docs](http://payex-checkout.readthedocs.org/)

### How to contribute:
* Fork this repo
* Contribute new `.md` files, or update existing ones cohering to the [Sphinx](http://sphinx-doc.org/) style.
* Create a pull-request for your changes.
* When merged, [Read The Docs](https://readthedocs.org/) will build and publish the new documentation.

### Build the documentation locally:
#### With vagrant
Not so intrusive. (and chosen by the main developer)
* Install [Vagrant](https://www.vagrantup.com/) and use `vagrant up` in the root directory.
This boots up a VM, gets the needed dependencies (listed in the native step below) and maps the VMs `/vagrant` to the root of the repository
* `vagrant ssh`
* `cd /vagrant/docs`
* `make html`
* The documentation will be created in the /docs/build/html directory on your host machine.

#### Native
* Install `python` and `python-pip`
* Install sphinx with `pip install sphinx`
* Install the markdown parser with `pip install recommonmark`
* Run `make.bat html` from the docs directory.
* The documentation will be created in the /docs/build/html directory of the repository.
