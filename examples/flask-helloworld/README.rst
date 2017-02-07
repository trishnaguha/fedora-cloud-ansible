Playbook to Run Containerized Flask Application on Atomic host
==============================================================

Configuration
-------------

Replace ``IP_ADDRESS_OF_REMOTE_HOST`` in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/flask-helloworld/examples/flask-helloworld/ansible/inventory#L2/>`_ file with the IP Address of your Remote Host.
Replace ``<PRIVATE_KEY_FILE>`` in ``ansible_ssh_private_key_file`` field in `Inventory <https://github.com/trishnaguha/fedora-cloud-ansible/blob/flask-helloworld/examples/flask-helloworld/ansible/inventory#L2/>`_ with your Private key file.
Replace ``<USER>`` in ``remote_user`` field in `ansible.cfg <https://github.com/trishnaguha/fedora-cloud-ansible/blob/flask-helloworld/examples/flask-helloworld/ansible/ansible.cfg#L3/>`_ with the user of your remote host.

Replace ``[Source Directory]`` in ``src_dir`` field in `main.yml <https://github.com/trishnaguha/fedora-cloud-ansible/blob/flask-helloworld/examples/flask-helloworld/ansible/main.yml#L7/>`_ with your ``/path/to/src_dir``.

Replace ``[Destination Directory]`` in ``dest_dir`` field in `main.yml <https://github.com/trishnaguha/fedora-cloud-ansible/blob/flask-helloworld/examples/flask-helloworld/ansible/main.yml#L7/>`_ with your ``/path/to/dest_dir``.

Run the Playbook
----------------

Now simply run ``ansible-playbook main.yml``. Make sure you are in `ansible directory <https://github.com/trishnaguha/fedora-cloud-ansible/tree/flask-helloworld/examples/flask-helloworld/ansible/>`_.

To verify the output execute the following command on your Atomic host:

``curl http://localhost:5000``.


Read more in this Blog Post: `http://www.projectatomic.io/blog/2016/10/deployment-using-ansible <http://www.projectatomic.io/blog/2016/10/deployment-using-ansible/>`_.
