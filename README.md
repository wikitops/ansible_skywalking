# Ansible : Playbook Skywalking

The purpose of this project is to deploy a standalone Skywalking server on a Linux Vagrant instance using Podman and an Elasticsearch standalone server as a backend.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

* [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
* Update the Vagrant file based on your computer (CPU, memory), if needed
* Update the operating system to deploy in the Vagrant file (default: CentOS 8)
* Install the Hostmanager Vagrant plugin

```bash
$ vagrant plugin install vagrant-hostmanager
```
* Download the Ansible requirements:

```bash
$ ansible-galaxy install -r requirements.yml
```
* Download the Ansible collection for Podman:

```bash
$ansible-galaxy collection install containers.podman
```

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Deployment

To deploy Skywalking on a Vagrant instance, just run this command :

```bash
$ vagrant up
```

If everything run as expected, you should be able to list the virtual machine created :

```bash
$ vagrant status

Current machine states:

skywalking01                   running (virtualbox)
```

If everything run as expected, you should be able to reach the Skywalking web interface : http://skywalking01:8080/

#### Destroy

To destroy the Vagrant resources created, just run this command :

```bash
$ vagrant destroy
```

### How-To

This section list some simple command to use and manage the playbook and the Vagrant hosts.

#### Update with Ansible

To update the Skywalking configuration with Ansible, you just have to run the Ansible playbook skywalking.yml with this command :

```bash
$ ansible-playbook skywalking.yml
```

#### Update with Vagrant

To update the Skywalking configuration with Vagrant, you just have to run provisioning part of the Vagrant file :

```bash
$ vagrant provision
```

#### Connect to Vagrant instance

To be able to connect to a Vagrant instance, you should use the CLI which is configured to automatically use the default SSH key :

```bash
$ vagrant ssh skywalking01
```

## Author

Member of Wikitops : https://www.wikitops.io/

## Licence

This project is licensed under the MIT License. For the full text of the license, see the [LICENSE](LICENSE) file.
