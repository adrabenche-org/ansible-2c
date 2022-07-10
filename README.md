# What 
Here you will find ansible scripts to deploy the following apps on a **standalone linux box**. Depending the situtation, **a new user named operator** will be created. Refef to `aws` or `do-vbox` README files for further information.

## Apps

Each app is implemented into a separate container providing the ability to decide which app do you want to install, and which not. Each app is attached to a role. You can find more information about how to setup each role inside the role folder for each cloud or environment.

- [x] Setup node: Setup basic stuff on the node.
    - [x] Support for Digital Ocean: By default we will use the Digital ocean droplets.
    - [x] Support for AWS: Add the features to support deploy on AWS instances
- [x] Cardano node: Install the Cardano node.
    - [x] Support for Digital Ocean: By default we will use the Digital ocean droplets.
    - [x] Support for AWS: Add the features to support deploy on AWS instances
- [x] Cardano cli: Install the cardano cli by pulling the docker image or building from this [github repo](https://github.com/adrabenche-org/yacc-builder.git)
- [ ] [Oura](https://github.com/txpipe/oura.git):  A implementation of a pipeline that connects to the tip of a Cardano node and submits Wto pluggable observers called "sinks".
    - [x] Support for Digital Ocean: By default we will use the Digital ocean droplets.
    - [x] Support for AWS: Add the features to support deploy on AWS instances
- [ ] [Scrolls](https://github.com/txpipe/scrolls.git): A tool for building and maintaining read-optimized collections of Cardano's on-chain entities.
    - [ ] Support for Digital Ocean: By default we will use the Digital ocean droplets.
    - [ ] Support for AWS: Add the features to support deploy on AWS instances

## Requirements

Before start

1) ssh access to the box, instance, droplet, etc you want to configure:
    * As root for **Digital Ocean** or **Virtual Box**
    * As ubuntu fo **AWS**
2) ansible installed. Access [this link](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) for documentation.

## How to deploy
First, install the ansible collection:
```bash
$ ansible-galaxy collection install -r ansible_collection.yml
```

Access the directory matching the cloud and look for the `README.md` file:

* **do-vbox**: Digital Ocean and Virtual Box. For Digital Ocean It's a minimal change on the device name when you are using a different filesystem fo the cardano database.
* **aws**: Amazon Web Services