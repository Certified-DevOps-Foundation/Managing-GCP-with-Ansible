# Managing-GCP-with-Ansible
This repo hosts some sample implementations which can help to create large scale cloud solutions and help ease the day to day tasks at work. 

# Why Ansible?
Ansible is a radically simple IT automation engine that automates cloud provisioning, configuration management, application deployment, intra-service orchestration, and many other IT needs.
Designed for multi-tier deployments since day one, Ansible models your IT infrastructure by describing how all of your systems inter-relate, rather than just managing one system at a time.
It uses no agents and no additional custom security infrastructure, so it's easy to deploy - and most importantly, it uses a very simple language (YAML, in the form of Ansible Playbooks) that allow you to describe your automation jobs in a way that approaches plain English.
[More on ansible basics.](https://www.ansible.com/overview/how-ansible-works)



# Pre-requisites
1. A GCP account
2. VM instances
3. Ansible setup

# Task 1
Creating and attaching a disk on GCP Compute Engine Instance and managing (partitioning, mounting, creating filesystem) it using Ansible
To create and attach a disk execute commands below.

## Use-case
Performing admin tasks related to disk management on the servers. For example creating filesystem and mounting SQL DB backups on the disks or getting the disks ready for application deployment on all the servers parallelly.



## Creating and attaching disks in GCP
```bash
gcloud compute disks create my-secondary-disk --size 10GB --type pd-standard --zone us-central1-a
gcloud compute instances attach-disk instance-template-1 --disk my-secondary-disk
```

## Images
These are screenshots of output of above commands.
![vm instances](/gcp-disk-setup/SS1.png "vm instances")
![vm instances](/gcp-disk-setup/ss2.png "vm instances")
![vm instances](/gcp-disk-setup/SS3.png "vm instances")

## Playbook execution setup
Use the something like used here [inventory](https://github.com/Certified-DevOps-Foundation/Managing-GCP-with-Ansible/blob/master/gcp-disk-setup/inventory).
Execute [disk-setup.yml](https://github.com/Certified-DevOps-Foundation/Managing-GCP-with-Ansible/blob/master/gcp-disk-setup/disk-setup.yml) playbook to complete the tasks such as partitioning, mounting and creating a filesystem.
Also have a look at the [ansible.cfg](https://github.com/Certified-DevOps-Foundation/Managing-GCP-with-Ansible/blob/master/gcp-disk-setup/ansible.cfg)
Output should be something like [output.txt](https://github.com/Certified-DevOps-Foundation/Managing-GCP-with-Ansible/blob/master/gcp-disk-setup/output.txt)

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## Authors
Contributed by Sajal Tyagi [LINKEDIN](https://www.linkedin.com/in/sajaltyagi/).

License
=======

GNU General Public License v3.0 or later
