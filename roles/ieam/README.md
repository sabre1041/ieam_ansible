ieam
=========

Installs and manages IBM Edge Application Manager (IEAM)

Requirements
------------

Docker must be installed on the target node


Role Variables
--------------

| Variable | Description | Required | Defaults |
|:---------|:------------|:---------|:---------|
|ieam_cluster_url| IEAM Cluster URL | yes | `` |
|ieam_username| Username | no | `iamapikey |
|ieam_api_key| API Key | yes | `` |
|ieam_organization| Organization | yes | `` |
|ieam_download_clis| Downloads CLI tools to the edge node  | no | `false` |
|ieam_node_name| Edge Node name  | no | `ansible_hostname` |
|ieam_pattern| Pattern  | no | `` |
|ieam_wait_for_service| Wait for Service  | no | `` |
|ieam_timeout| Timeout for registration to complete  | no | `` |
|ieam_action| Action to perform  | no | `register` |

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: ieam
      become: true
      tasks:
         - name: Manage IEAM
           include_role:
             name: ieam

License
-------

Apache 2

Author Information
------------------

Andrew Block <ablock@redhat.com>
