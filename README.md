# Hashicorp Vault setup using Ansible Role

We are going to create an Ansile Role for Vault setup so we can reuse it. We will begin by creating a new user account named "vault" which will help with a secure setup. We will use this account to isolate the ownership of vault. We don't create any home directory or shell for this user so that user can't log in to a server.

Next, we need to download vault archive from here on our remote vault instance. This will give a zip archive file. To unzip vault archive, we need to install unzip so we can unzip vault archive and takeout needed binary. Once this is done, we need to unzip vault archive, move our vault binary to "/usr/local/bin" and make vault user as the owner of this binary with reading and execute permissions.

We need to set binary capabilities on Linux, to give the Vault executable the ability to use the mlock syscall without running the process as root.

We need to setup systemd init file to manage the persistent vault daemon. We need to set below content into systemd service file. Finally, start the vault server.

### Setup

Provide server IP address in the inventory file on which we want to run this playbook. As we are using S3 as Vault backend, please provide access_key and secret_key in vault.hcl.j2 file in templates of vault role.

Once done run command:

ansible-playbook playbook.yml
