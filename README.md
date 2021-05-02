# ansible-playbooks

[![CI](https://github.com/PaloAltoNetworks/ansible-playbooks/actions/workflows/ci.yml/badge.svg)](https://github.com/PaloAltoNetworks/ansible-playbooks/actions/workflows/ci.yml)

Example Ansible playbooks using the Palo Alto Networks
[Ansible Collection](https://github.com/PaloAltoNetworks/pan-os-ansible), and what you'll need to get started writing
your own.  We try to add interesting things to this repository over time based on customer questions, so check back
from time to time.

## Getting Started

### Installing Ansible

First, you'll need to install Ansible on the machine that will execute your playbooks (called the control node).  The
control node can be as simple as a laptop, and can be running any Unix-like OS (Linux, BSD, macOS).

You'll want to generally follow the
[Ansible documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-the-control-node)
for installing Ansible on your machine, but here are quick instructions for popular choices:

#### CentOS

Install from [EPEL](https://fedoraproject.org/wiki/EPEL):

```
$ sudo yum install epel-release
$ sudo yum install ansible
```

#### Ubuntu

Install from the Ansible PPA:

```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

#### macOS 10.15

Install from Pip (Python package manager):

```
$ pip3 install --user ansible
$ export PATH=$PATH:$HOME/Library/Python/3.7/bin
```

You'll want to permanently modify the PATH in your shell's config file as well.

### Clone this repository, install PAN-OS Collection

Once you're done with installing Ansible, clone this repo, and install the PAN-OS collection from Ansible Galaxy
as well as the Python modules it depends on:

```
$ git clone https://github.com/PaloAltoNetworks/ansible-playbooks.git
$ cd ansible-playbooks/
$ ansible-galaxy collection install -r collections/requirements.yml
$ pip3 install --user -r requirements.txt
```

### Customize connection parameters

The supplied inventory sets variables for each host in the `host_vars` directory.  Authentication credentials are not
included, and should be specified either on the CLI, or in a seperate file like so:

```
$ ansible-playbook -i inventory check_ready.yml -e @creds.yml
```

You're now ready to start using these playbooks.

## Sample Playbooks

You can use these playbooks as a base by cloning this repository.  Each of them is documented with how to run them via
`ansible-playbook` and their customization options.

* check_ready.yml - Checks to see if a firewall is ready via 'show chassis-ready' command.
* download_panos_version.yml - Downloads a PAN-OS version to a device.
* fw_config_lock.yml - Handle firewall config locking.
* fw_objects.yml - Create various objects on a PAN-OS device.
* fw_rule_survey.yml - Add security rule via Ansible Tower survey.
* fw_rules.yml - Create security rules on a PAN-OS device.
* fw_shutdown.yml - Shuts down a PAN-OS device.
* session_report.yml - Generates a report on long sessions.
* show_changes.yml - Checks for uncommitted changes and commits if necessary.
* upgrade_content.yml - Upgrade the content version on a PAN-OS device.
* upgrade_ha.yml - PAN-OS HA pair upgrade playbook.
* upgrade_ha_major.yml - PAN-OS HA pair major version upgrade playbook.
* upgrade_panorama_ha.yml - Panorama HA upgrade playbook.
* upgrade_panorama_ha_major.yml - Panorama HA major version upgrade playbook.
* upgrade_single.yml - PAN-OS single firewall upgrade playbook.
* upgrade_single_major.yml - PAN-OS single firewall major version upgrade playbook.
