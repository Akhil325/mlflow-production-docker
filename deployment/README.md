# MLflow Provision and Deploy

Set up an Ubuntu server to run the [mlflow-production-docker](https://github.com/jameswilliams1/mlflow-production-docker) package.

## Setup

- Ensure your public key is present in your servers [authorized_keys file](https://www.ssh.com/ssh/authorized_keys/openssh/)
- Install Ansible locally: `pip3 install --user ansible`
- Add a host named `mlflow` to your [Ansible inventory file](https://docs.ansible.com/ansible/latest/network/getting_started/first_inventory.html#basic-inventory) pointing to your server's IP address/domain (Two example inventory files `hosts-local.yml` and `hosts-deployment.yml` are provided - ensure you change address's if you use these files)

## Provision

The following configures the server by installing all required dependencies.

From the root directory run:

```sh
ansible-galaxy install -r deployment/requirements.yml
ansible-playbook -i hosts-deployment.yml deployment/provision.yml
```

## Deploy

The following will copy this repository (entire root repo) to the remote servers and create and run all the services.

From the root directory run:

```sh
ansible-playbook -i hosts-deployment.yml deployment/run.yml
```
