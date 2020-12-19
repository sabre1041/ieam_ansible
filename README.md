# ieam_ansible

Ansible automation to manage an edge node using IBM Edge Application Manager (IEAM)

## Components

The following assets are found in this repository

* Roles
  * [docker_ce](roles/docker_ce) - Installs Docker Community Edition
  * [ieam](roles/ieam) - Installs and manages IEAM
* Playbooks
  * [ieam.yml](playbooks/ieam.yml)
* [Inventory](inventory)

## Quickstart

The following steps will demonstrate how to make use of the assets contained in this repository

### Prerequisites

Edge devices must be subscribed in order to install necessary dependencies

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

### Playbook Execution

Execute the playbook to provision the edge nodes:

```
$ ansible-playbook -i inventory/ playbooks/ieam.yml -e @ieam-vars.yml
```

### Teardown (Optional)

To unregister the nodes, execute the following command:

```
$ ansible-playbook -i inventory/ playbooks/ieam.yml -e @ieam-vars.yml -e ieam_action=unregister
```