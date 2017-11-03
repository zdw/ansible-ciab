# Ansible playbook to mass-deploy CORD

> NOTE that this tool is not supported by opencord. No maintenance guarantee
> are given

For any information about CORD please refer to the [Opencord
Guide](guide.opencord.org)

This playbook will start a tmux session on the target server and run the
commands to install CORD in it.  Once the playbook has executed, to check the
installation process, you can connect to the server and attach the `tmux`
session.


## How to use

### Create an inventory file

Create an [ansible inventory
file](http://docs.ansible.com/ansible/latest/intro_inventory.html) in
`inventory` and add your server address.

### Set Configuration

Open `deploy-cord-settings.yml` and edit as needed. Gerrit patches and
additional `make` targets to run after `config` and `build` can be added.

### Run

Execute the playbook with:

    ansible-playbook -i inventory/<your inventory file> deploy-cord.yml

### Connect

SSH to the node, then run:

    tmux attach

When the build is finished, the `tmux` session will end.  See the logs in `~`
to check the build status if this has happened.


# Running one-off commands with ansible

You can run a one-off command across your cluster as well - for example:

    ansible -i inventory/<inv file> -m ping all

    ansible -i inventory/<inv file> -b -m apt -a "update_cache=yes upgrade=dist" all

    ansible -i inventory/<inv file> -b -m command -a "shutdown -r now" all

    ansible -i inventory/<inv file> -m shell -a "cd ~/cord/build; make clean-all; cd ~; rm -rf cord* 2017* build.log" all


