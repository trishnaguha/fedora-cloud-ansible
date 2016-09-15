Playbook To Run Cockpit Container on Atomic Host
================================================

Pre-Configuration
-----------------

Replace ``IP_ADDRESS_OF_REMOTE_HOST`` in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/5fd668e71742771a536bf41d9346fb255f8455fe/cockpit/inventory#L2/>`_ file with the IP Address of your Remote Host.
Replace ``<USER>`` in ``remote_user`` field in `ansible.cfg <https://github.com/trishnaguha/fedora-cloud-ansible/blob/5fd668e71742771a536bf41d9346fb255f8455fe/cockpit/ansible.cfg#L3/>`_ with the user of your remote host.

Run The Playbook
----------------

Now simply run ``ansible-playbook cockpit.yml``.


Visit your ``IP_Address:9090`` on your web browser :).

``Port:9090`` is default PORT of Cockpit Container.
