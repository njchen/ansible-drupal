# Ansible provisioning for Drupal

[![Latest Version](https://img.shields.io/github/release/netsensei/ansible-drupal.svg?style=flat-square)](https://github.com/netsensei/ansible-drupal/releases)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)

## Ansible provisioning for Drupal

This project provides [Ansible](http://www.ansible.com) provisinioning for easy/quick installation and configuration of a LAMP stack which supports [Drupal 8](http://drupal.org). This ansible playbook has been generated via [Phansible](phansible.com) and tweaked.


### Requirements

You will need a working installation of [Vagrant](https://www.vagrantup.com/) and [Ansible](http://www.ansible.com) on your machine.

### What is in the box?

- Ubuntu Trusty Thar 14.04
- 512Mb RAM
- NGinX based
- PHP 5.6 with a few required extensions
- MySQL database
- [Drupal console](https://drupalconsole.com/)
- [Drush](http://www.drush.org/en/master/)
- [Composer](https://getcomposer.org/)

## Install

Clone this repository to your local machine (we assume you have a dedicated workspace folder at `~/Workspace` refer to `Vagrantfile` to change this to a destination of your choice.)

Install Drupal first:

```bash
cd ~/Workspace
drush dl drupal
```

Change the pointer in the `Vagrantfile` to the folder where Drupal was installed:

`config.vm.synced_folder "~/Workspace/drupal8", "/vagrant", type: "nfs"`

Next, you should create a `sites/default/files` folder and copy example.settings.php to
a new settings.php file. Make sure both are rewritable.

```bash
cd ~/Workspace
git clone https://github.com/netsensei/ansible-drupal ~/Workspace
cd ~/Workspace/ansible-drupal
vagrant up
```

## Usage

Out of the box, NGinX listens on IP address `192.168.88.88`. Alternatively, you could create an entry in your `/etc/hosts` file that points to `drupal.app`.

Open up your browser and navigate to either the IP address or the local domain. First time, you should be welcomed by the Drupal installer.

Database details:

- User: Drupal
- Password: Drupal
- Database: Drupal

## NFS issues

If you run into mounting shared folders issues on El Caption, here are some pointers:

- Make sure you run Virtualbox 4.3. I've run into trouble with 5.x versions.
- Make sure you've installed the VBox 4.3 guest additions.
- Reboot your Mac entirely.
- Destroy the entire vagrant box and build it again.

## Documentation

## Security

If you discover any security related, please email matthias@colada.be instead of using the issue tracker.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
