# Airtime Appliance Deployment

This is an example of an Airtime Chef automated deployment, that we use internally for easily testing new releases and features. 

This is **NOT** meant for production use.

It uses Opscode Chef (solo) 11.x and Librarian-Chef.

Software includes apache2, php5, icecast2, postgresql, airtime.

## Prerequisites

* [Virtualbox](https://www.virtualbox.org/) or VMware Fusion
* [Vagrant](http://downloads.vagrantup.com/) and a Ubuntu Box (there's an excellent [Vagrant VMware plugin](http://www.vagrantup.com/vmware))
* a working ruby dev environment with bundler: try [homebrew](http://brew.sh) for a good start
* [Vagrant-Bindle](https://github.com/fgrehm/bindler) to handle Vagrant plugins.
* a working ruby dev environment: try [homebrew](http://brew.sh) for a good start on OSX

## Install

### Vagrant Environment
You need to have [Vagrant-Bindle](https://github.com/fgrehm/bindler) installed: 

```
$ vagrant plugin install bindler
$ vagrant bindler setup
```

Install automatically required Vagrant plugins:

``
$ vagrant plugin bundle
``

### Chef Development Environment

If you need to hack on cookbooks, you might need Chef binaries, tools and plugins.

Launch bundler: 

````
$ bundle install --binstubs
$ ./bin/librarian-chef install
````

## Launch 

This is an example to launch the default "airtime" Vagrant profile. 

* VMware Fusion

``
$ vagrant up airtime --provider=vmware_fusion
``

* VirtualBox

``
$ vagrant up airtime --provider=virtualbox
``

## Web Access

Access your new Airtime installation: 

* Airtime web GUI: [http://localhost:8080](http://localhost:8080)
* Icecast stream: [http://localhost:8000/airtime_128](http://localhost:8000/airtime_128)

## SSH Access

If needed, you can access the box by SSH.

````
$ vagrant ssh
````

## Optional Configuration Steps

### Timezone

Airtime timezone is optionnaly to be configured

## Chef Roles dependencies

(updated by issuing `knife role spaghetti`)

![Airtime Chef Roles Dependencies Graph][1]
[1]: ./role-spaghetti.png "Airtime Chef Roles Dependencies Graph"

