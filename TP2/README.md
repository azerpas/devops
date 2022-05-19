[← Menu](../README.md)

# TP2 - AMI with Ansible and Packer

# Ansible
Agentless management of infrastructure

From the control node (master), manages machines (slaves) and other devices remotly with SSH.

## Playbooks

Playbooks execute Ansible configuration, deployment, and orchestration functions on slave machines. They are written in YAML and are executed by the Ansible command line tool. 

For example it can automate the installation and configuration of a web server:
- Install Apache
- Change port
- Delete Apache default website 
- Deploy a website
- Restart Apache

# Packer
Tool for creating identical images of machines for multiple platforms (AWS, Azure, ...) and from a single configuration.

These images will then be used by other tools (Ansible, Puppet, Chef, Shell) to automate the deployment of these images to different platforms.

## Builder
Builders create machines and generate images from those machines for various platforms.

## Provisionner
Provisioners use builtin and third-party software to install and configure the machine image after booting.