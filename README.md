# Ansible automation to deploy CORD-in-a-Box

> NOTE that this tool is not supported by opencord. No mainteinance guarantee are give.

For any information about `CiaB` please refer to the [Opencord Guide](guide.opencord.org)

## How to use it

**Configure your server**

Open `inventory/cloudlab` and list your server address there

**Configurations**

Open `ciab-setting.yml` and edit it as needed, note that you can list as many patches as you want in there and you can add `make` targets to be executed after `config` and `build`.

**Run**

Execute it with `ansible-playbook -i inventory/cloudlab deploy-ciab.yml`