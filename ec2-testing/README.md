# Provision a Red Hat OpenShift Cluster on AWS

This repository contains a set of playbooks and roles which provisions and deprovisions an Amazon EC2 instance acting as a jump server and a Red Hat OpenShift Cluster on AWS. The Amazon EC2 jump server serves as the management server from where we ran the OpenShift installer and CLI tasks.

The playbooks build all the required components (including VPC, networking, security groups, etc.), and you can modify the `vars/main.yml` file to use different defaults if you'd like.

## Usage

Make sure you have `boto3` and `botocore` installed locally: `pip3 install boto3 botocore`.

Install requirements:

```
$ ansible-galaxy install -r requirements.yml
```

Build the Amazon EC2 jump server:

```
$ ansible-playbook build.yml
```

Provision a Red Hat OpenShift Cluster on AWS in the environment:

```
$ ansible-playbook openshift_install.yml
```

## Cleanup

Once you don't need anymore the setup, run the `destroy.yml` playbook to destroy the test environment:

```
$ ansible-playbook destroy.yml
```
