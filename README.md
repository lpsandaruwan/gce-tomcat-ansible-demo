# gce-tomcat-ansible-demo
Tomcat deployments in GCE using Ansible

### Prerequisites
* Python 2.6 or above with python-dev and python-pip packages
* apache-libcloud python package
* Google cloud platform billable account, a project and a service account with appropriate roles and permission

### Install required software
Make sure that you have installed Python 2 and python-dev packages and python-pip.

#### Install required python packages
```bash
pip install -r requirements.txt
```
### Configurations and preparations

#### Google Cloud Platform related
Make sure that have a Google Cloud Platform account and the billing is enabled, see [https://cloud.google.com](https://cloud.google.com)
* Follow this guide to create new Google Cloud Platform projects, [https://cloud.google.com/resource-manager/docs/creating-managing-projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects)
* Create a new service account and obtain a JSON formatted private key for the account, see [https://cloud.google.com/iam/docs/creating-managing-service-account-keys](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)
* To setup SSH keys to access GCE instances, simply use Google Cloud SDK tools, [https://cloud.google.com/sdk/gcloud/reference/compute/config-ssh](https://cloud.google.com/sdk/gcloud/reference/compute/config-ssh) 
or create SSH keys(see [https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#createsshkeys](https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#createsshkeys)) 
and add them as metadata(see [https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys](https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys))
* Then configure the `gce_vars/authentication` by giving the project id, obtained JSON key file location for the new GCP project and the created service account email.
* For the configurations of `gce_vars/instance`, refer [https://cloud.google.com/compute/docs/regions-zones](https://cloud.google.com/compute/docs/regions-zones/), 
[https://cloud.google.com/compute/docs/machine-types](https://cloud.google.com/compute/docs/machine-types), 
[https://cloud.google.com/compute/docs/images](https://cloud.google.com/compute/docs/images) for zones, machine types and image types respectively. 
Also configure the allowed_ports for HTTP traffic to be enabled on given ports.

#### Roles related
* To configure installation of Java, Tomcat and deployment related metadata refer `defaults/main.yml` of each role.

### Run playbook
* Set environment variables.
```bash
export ANSIBLE_HOSTS=hosts
```

* All done. Now run the playbook and see.
```bash
ansible-playbook run.yml
```
