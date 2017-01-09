Talk to Docker Daemon of Atomic Host
====================================

This ansible playbook describes how to use [Docker](https://www.docker.com/) daemon of Atomic host remotely.Note that we are also going to secure the Docker daemon with TLS since we are connecting via Network.
Before you carry on with the following steps keep in mind that ANY process on the client that can access the TLS certs now has FULL root access on the server and can do anything it wants to do. Therefore we will want to give access of Docker daemon of server only to the specific client host that can be trusted.

I am using [Fedora-Atomic](https://getfedora.org/en/atomic/) host as remote(Docker Daemon host) and [workstation](https://getfedora.org/en/workstation/download/) as my present host(Docker Client host).

Thanks to [Chris Houseknecht](https://twitter.com/CHouseknecht) for writing an [Ansible](https://www.ansible.com/) role which creates all the certs required automatically, so that there is no need to issue `openssl` commands manually. Here is the Ansible role repository: [role-secure-docker-daemon](https://github.com/ansible/role-secure-docker-daemon).

##Steps

Clone the [reposiroty](https://github.com/trishnaguha/fedora-cloud-ansible).

```
$ git clone https://github.com/trishnaguha/fedora-cloud-ansible.git
```

Now

```
$ cd docker-remote-access
```

Clone the Ansible role: [https://github.com/ansible/role-secure-docker-daemon](https://github.com/ansible/role-secure-docker-daemon)

```
$ git clone https://github.com/ansible/role-secure-docker-daemon.git
$ ls
ansible.cfg  inventory  remote-access.yml  role-secure-docker-daemon
```

Replace **IP_OF_ATOMIC_HOST** and **PRIVATE_KEY_FILE** in **inventory** with the IP of your Atomic host and ssh private key file of your workstation respectively.

Run the playbook after that.

```
$ ansible-playbook remote-access.yml
```

Make sure `tcp port 2376` in opened of your atomic instance. If you are using Openstack, add the tcp port in your security rule.
Reboot both of your Atomic host(Docker Daemon host) and Workstation(Docker Client host).

So now if you try running any docker command as regular user on your workstation it will talk to the docker daemon of the Atomic host and execute the command there. You do not need to manually ssh and issue docker command on your Atomic host.


##Here is the directory structure for better clarification:

```
$ tree docker-remote-access/
docker-remote-access/
├── ansible.cfg
├── inventory
├── remote-access.yml
└── role-secure-docker-daemon
```
The Ansible role goes inside the directory.
