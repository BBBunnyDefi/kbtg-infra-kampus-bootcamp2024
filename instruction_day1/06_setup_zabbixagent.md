# 06_setup_zabbixagent
The Zabbix Agent is a crucial component of the Zabbix monitoring system, responsible for collecting data from the systems it runs on and sending that information to the Zabbix Server for processing. Here's an overview of the Zabbix Agent:

## Objectives
- Setup Zabbix Server for monitoring metrics on your system.

## Expected Outcome
- The Zabbix Agent is ready to use, and the Zabbix server can collect metrics for all EC2 machines.

## Prerequisites
- Must finish task
    - 04_setup_ansible
    - 05_setup_zabbixserver

## Installation
> [!NOTE]
> The following instruction for the [helper] only.

Use this Ansible playbook YAML to install the Zabbix Agent on all your machines.

Should be Prepare install_zabbix-agent2.yml file from assets\install_zabbix-agent2.yml

Execute following command
```sh
ansible-playbook -i hosts install_zabbix-agent2.yml
```

## Verify
> [!NOTE]
> The following instruction for the non [helper] server only.
Check zabbix-agent on another machines

```sh
systemctl status zabbix-agent
```
The response should be like this:
```sh

```
