Playbook To Run Cockpit Container on Atomic Host
================================================

Pre-Configuration
-----------------

Replace ``IP_ADDRESS_OF_REMOTE_HOST`` in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/cockpit/inventory#L2/>`_ file with the IP Address of your Remote Host.
Replace ``<USER>`` in ``ansible_ssh_user`` field in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/cockpit/inventory#L2/>`_ with username of Host.
Replace ``<PRIVATE_KEY>`` in ``ansible_ssh_private_key_file`` field in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/cockpit/inventory#L2/>`_ with your Private key file.
Replace ``<USER>`` in ``remote_user`` field in `ansible.cfg <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/cockpit/ansible.cfg#L3/>`_ with the user of your remote host.

Run The Playbook
----------------

Now simply run ``ansible-playbook cockpit.yml``.


Visit your ``IP_Address:9090`` on your web browser :).

``Port:9090`` is default PORT of Cockpit Container.

**NOTE**: If you are using Openstack make sure your security group has ``PORT`` open to ``9090``.
