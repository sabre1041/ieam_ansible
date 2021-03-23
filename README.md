# ieam_ansible

Ansible automation to manage the deployment of IBM Edge Application Manager (IEAM) in edge environments

## Components

The following assets are found in this repository

* Roles
  * [docker_ce](roles/docker_ce) - Installs Docker Community Edition on edge devices
  * [ieam](roles/ieam) - Installs and manages IEAM on an edge device and OpenShift cluster
* Playbooks
  * [ieam.yml](playbooks/ieam.yml)
* [Inventory](inventory)

## Quickstart

The following steps will demonstrate how to make use of the assets contained in this repository

### Prerequisites

The following conditions must be met prior to running the automation:

* Cluster
  * An OpenShift Container Platform with `cluster-admin` privileges
* Device
  * A Linux machine. When installing on Red Hat Enterprise Linux (RHEL), the machine must be subscribed.

### Populate Inventory

Populate the inventory of edge devices by filling in the `ieam` group in the [hosts](inventory/hosts) file

### Create Variables file

Create a file called `ieam-vars.yml` that will contain the necessary variables in order to configure the edge devices with the following content.

```
ieam_cluster_url: "https://<cluster_url>"
ieam_api_key: "<api_key>"
ieam_organization: "<organization_id>"
ieam_pattern="IBM/pattern-ibm.helloworld"
ieam_wait_for_service="*"
ieam_wait_for_timeout=120
```

Be sure to replace the content with values from your environment.

By default, IEAM will be configured to deploy on an edge OpenShift cluster. To deploy on an edge device instead, set the `ieam_install_mode` variable to `device`.


### Playbook Execution

Execute the playbook to provision the edge nodes:

```
$ ansible-playbook -i inventory/ playbooks/ieam.yml -e @ieam-vars.yml
```

### Teardown (Optional)

To unregister an edge node, execute the following command:

```
$ ansible-playbook -i inventory/ playbooks/ieam.yml -e @ieam-vars.yml -e ieam_action=unregister
```