docker_ce
=========

Installs Docker Community Edition

Requirements
------------

None

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: ieam
      become: true
      tasks:
         - name: Install Docker CE
           include_role:
             name: docker_ce

License
-------

Apache 2

Author Information
------------------

Andrew Block <ablock@redhat.com>
