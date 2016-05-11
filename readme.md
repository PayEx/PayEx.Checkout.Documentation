# PayEx Checkout Documentation

[![Join the chat at https://gitter.im/PayEx/Checkout.Documentation](https://badges.gitter.im/PayEx/Checkout.Documentation.svg)](https://gitter.im/PayEx/Checkout.Documentation?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
![read the docs build](https://readthedocs.org/projects/payex-checkout/badge/?version=latest)

This repository contains the source code for [the documentation of PayEx Checkout](http://payex-checkout.readthedocs.io/en/latest/).

**The PayEx Checkout service is in private beta and is currently not available to the general public.**



## How to contribute:
The easiest way is to navigate to the file you want to edit in the [docs](docs) directory and edit it directly here on GitHub. If you want to do more extensive editing such as adding an entirely new file, you can, instead:

* [Fork](https://guides.github.com/activities/forking/) this repository
* Contribute new `.md` files, or update existing ones following the [MkDocs](http://www.mkdocs.org/user-guide/writing-your-docs/#writing-your-docs) style.
* Create a [pull-request](https://help.github.com/articles/creating-a-pull-request/) for your changes.
* When merged, [Read The Docs](https://readthedocs.org/) will build and publish the new documentation.

## Build the documentation locally

### Native
* Install `python` and `python-pip`
* Install mkdocs with `pip install mkdocs`
* Run `mkdocs build` from the root directory.
* The documentation will be created in the /site directory of the repository.
* Use `mkdocs serve` and browse to `http://localhost:8000/` to see the site.

### With Vagrant
* Install [Vagrant](https://www.vagrantup.com/) and use `vagrant up` in the root directory.
This boots up a VM, gets the needed dependencies (listed in the native step below) and maps the VMs `/vagrant` to the root of the repository
* `vagrant ssh`
* `cd /vagrant/docs`
* `mkdocs build`
* The documentation will be created in the `/site` directory on your host machine.
