Talk to Docker Daemon of Atomic Host
====================================

This ansible playbook describes how to use [Docker](https://www.docker.com/) daemon of Atomic host remotely.  Note that we are also going to secure the Docker daemon since we are connecting via Network which we will be doing with TLS.

TLS (Transport Layer Security) provides communication security over computer network. We will create client cert and server cert to secure our Docker daemon. OpenSSL will be used to to create the cert keys for establishing TLS connection.

I am using [Fedora-Atomic](https://getfedora.org/en/atomic/) host as remote and [workstation](https://getfedora.org/en/workstation/download/) as my present host.

Thanks to [Chris Houseknecht](https://twitter.com/CHouseknecht) for writing an [Ansible](https://www.ansible.com/) role which creates all the certs required automatically, so that there is no need to issue openssl commands manually. Here is the Ansible role repository: [role-secure-docker-daemon](https://github.com/ansible/role-secure-docker-daemon).

##Steps

Clone the [reposiroty](https://github.com/trishnaguha/fedora-cloud-ansible).

```
$ git clone https://github.com/trishnaguha/fedora-cloud-ansible.git
```

Now

```
$ cd docker-daemon-remote-access
$ cd docker-client
```
Replace **IP_OF_ATOMIC_HOST** in **clientsetup.yml** with the IP address of atomic host.
Run the playbook thereafter.

```
$ ansible-playbook clientsetup.yml
```

The above playbook will create **~/.docker** directory on workstation where the client certs will lie. It also adds Environment variables in **~/.bashrc** file which will be required for the workstation to use to the Docker daemon of atomic host.

Now Change your directory to the **docker-daemon** directory.
Clone the Ansible role: [https://github.com/ansible/role-secure-docker-daemon](https://github.com/ansible/role-secure-docker-daemon)

```
$ cd ..
$ cd docker-daemon
$ git clone https://github.com/ansible/role-secure-docker-daemon.git
$ ls 
ansible.cfg  inventory  remote-access.yml  role-secure-docker-daemon
```

Replace **USER_NAME** in **docker-daemon/ansible.cfg** with the user of your Atomic host, **IP_OF_ATOMIC_HOST** and **PRIVATE_KEY_FILE** in **docker-daemon/inventory** with the IP of your Atomic host and ssh private key file of your workstation respectively.

Run the playbook after that.

```
$ ansible-playbook remote-access.yml
```

Make sure tcp port 2376 in opened of your atomic instance. If you are using Openstack, add the tcp port in your security rule.
Reboot both of your Atomic host and Workstation.

So now if you try running any docker command as regular user on your workstation it will talk to the docker daemon of the Atomic host and execute the command there. You do not need to manually ssh and issue docker command on your Atomic host.


##Here is the directory structure for clarification:

```
docker-daemon-remote-access/
├── docker-client
│   ├── ansible.cfg
│   ├── clientsetup.yml
│   └── inventory
├── docker-daemon
│   ├── ansible.cfg
│   ├── inventory
│   └── remote-access.yml
└── README.md
```
