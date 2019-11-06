---
title: "Setup Collaboration"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 6
summary: Guideline for deploying seafile with ansible.
---

One big aspect is sharing and collaborating documents. From our perspective the following conditions are essential:

- Stable and fast client (Sync)
- End-to-end-encryption
- Open-Source
- Revision / version history
- Easy to install / simple to configure

Unfortuantely LEL currently does not support all of these requirements, but syncing folders is enough, since every document is plain markdown and the computing is done dynamically.

The good thing there are alternatives which fit this space and work fantastically together with LeL :)

- [Seafile](https://github.com/haiwen/seafile) is my personal favorite, and therefore the setup is completly automated and be found in the [github repository](https://github.com/c-f/lel/_lel-ansible-playbook/).

## Overview

Afterwards you can use Ansible to install and configure seafile.

Ansible will install all dependencies, then build the seafile image and start seafile as a persistent docker container. Afterwards the users and the e2e encrypted docmentation is created.

**NOTE**:
Please be aware that the password is sent on the server unencrypted `once!` to the container on the same machine. However if you do not trust your cloud provider, then setup the container locally and just upload the initialized container.

## Deployment

**Note**: If you are unfamilliar with _ansible_ here a few resources:

- https://medium.com/@denot/ansible-101-d6dc9f86df0a
- https://www.redhat.com/en/blog/ansible-101-part-1-beginning-there-was-yaml
- https://docs.ansible.com/ansible/2.7/index.html

**Skip this until 4. if you are familliar with ansible**

1. Just spin up a small linux instance by your favorite Cloud-provider.
2. Install ansible. The `_lel-ansible-playbook/setup.sh` file creates a new virtual environment, with **ansible 2.7**.

```bash
sil@pandora:/tmp/LeL_v0.0.1_linux_amd64$ cd _lel-ansible-playbook/
sil@pandora:/tmp/LeL_v0.0.1_linux_amd64/_lel-ansible-playbook$ ./setup.sh

[*] Check for Virtual ansible envrionment

[+] Install Ansible to: /ansible2.7
Running virtualenv with interpreter /usr/bin/python2

[...]

# enable the virtualenv
sil@pandora:/tmp/LeL_v0.0.1_linux_amd64/_lel-ansible-playbook$ source ansible2.7/bin/activate
```

3. Copy the `sample.inv.yml` to `inv.yml` and change the ip address to your server.
4. Modify the `misc_docu_srv._usernames.yml` for your teammember. These accounts will be created and grant privileges for the end-to-end encrypted repository.

```bash
operators:
 - lel@my.l3l.lol
```

5. Start the ansible playbook with the options you need

```bash
(ansible-2.7) sil@pandora:/tmp/LeL_v0.0.1_linux_amd64/_lel-ansible-playbook$ ansible-playbook -i inv.yml --private-key ~/.ssh/SSHKEY.pem -k sync-server.yml
```

![pic](/user/pic_ansible.png)

6. If you see no errors then congratulation - seafile is installed, up and running and the setup was executed. All the passwords are stored now inside the `seafile.release.txt` file:

```
---------------------
End2end: <some-random-32-passowrd>
Admin_PW: <some-random-32-passowrd>
Operator: <name>:<some-random-32-passowrd>
```

7. In order to connect to the seafile server it is first necessary to foward the service, since by default it listen only on 127.0.0.1:13331. The forward can simply be done via a SSH-Config

```bash
// inside the $HOME/.ssh/config
Host docu
	Hostname <ip>
	User <user>
	IdentityFile <some-path-to-the-private-key>
	LocalForward 127.0.0.1:13331 127.0.0.1:13331

```

8. Now seafile can be access via the browser at `127.0.0.1:13331`. Additionally the seafile client can be used. It can be installed via the official homepage. Afterwards the credentials can be entered and the folder can be synced.

If you don't want to install the client you can also run it inside a docker container. The setup and configuration can be found in the `README` on the server.

**Note**: More information can be found inside the README.md file on the server.
