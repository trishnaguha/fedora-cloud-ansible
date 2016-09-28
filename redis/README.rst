Playbook To Run Redis Container on Atomic Host
==============================================

Configuration
-------------

Replace ``IP_ADDRESS_OF_REMOTE_HOST`` in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/redis/inventory#L2/>`_ file with the IP Address of your Remote Host.
Replace ``<USER>`` in ``ansible_ssh_user`` field in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/redis/inventory#L2/>`_ with username of Host.
Replace ``<PRIVATE_KEY_FILE>`` in ``ansible_ssh_private_key_file`` field in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/redis/inventory#L2/>`_ with your Private key file.
Replace ``<USER>`` in ``remote_user`` field in `ansible.cfg <https://github.com/trishnaguha/fedora-cloud-ansible/blob/master/redis/ansible.cfg#L3/>`_ with the user of your remote host.

Run The Playbook
----------------

Now simply run ``ansible-playbook httpd.yml``.
