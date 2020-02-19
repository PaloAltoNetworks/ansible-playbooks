# ansible-pan-samples

[![ansible-lint](https://github.com/mrichardson03/ansible-pan-samples/workflows/ansible-lint/badge.svg)](https://github.com/mrichardson03/ansible-pan-samples/actions?query=workflow%3Aansible-lint)

Example Ansible playbooks using the Palo Alto Networks [modules](https://ansible-pan.rtfd.io), and what you'll need to
get started writing your own.  I try to add interesting things to this repository over time based on customer
questions, so check back from time to time.

## Getting Started

### Installing Ansible

First, you'll need to install Ansible on the machine that will execute your playbooks (called the control node).  The
control node can be as simple as a laptop, and can be running any Unix-like OS (Linux, BSD, macOS).

You'll want to generally follow the
[Ansible documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-the-control-node) for installing Ansible on your machine, but here are quick
instructions for popular choices:

#### CentOS 7

Install direct from Ansible:

```
$ sudo rpm install -i https://releases.ansible.com/ansible/rpm/release/epel-7-x86_64/ansible-2.9.4-1.el7.ans.noarch.rpm
```

#### Ubuntu 18.04

Install from the Ansible PPA:

```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

#### macOS 10.14

Install from Pip (Python package manager):

```
$ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
$ python get-pip.py --user
$ pip install --user ansible
$ export PATH=$PATH:$HOME/Library/Python/2.7/bin
```

You'll want to permanently modify the PATH in your shell's config file as well.

### Installing PAN-OS Collection

Once you're done with installing Ansible, install the PAN-OS collection from Ansible Galaxy:

```
$ ansible-galaxy collection install -r collections/requirements.yml
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
* upgrade_single.yml - PAN-OS single firewall upgrade playbook.

## Support Policy

The code and templates in the repo are released under an as-is, best effort,
support policy. These scripts should be seen as community supported and
Palo Alto Networks will contribute our expertise as and when possible.
We do not provide technical support or help in using or troubleshooting the
components of the project through our normal support options such as
Palo Alto Networks support teams, or ASC (Authorized Support Centers)
partners and backline support options. The underlying product used
(the VM-Series firewall) by the scripts or templates are still supported,
but the support is only for the product functionality and not for help in
deploying or using the template or script itself. Unless explicitly tagged,
all projects or work posted in our GitHub repository
(at https://github.com/PaloAltoNetworks) or sites other than our official
Downloads page on https://support.paloaltonetworks.com are provided under
the best effort policy.
