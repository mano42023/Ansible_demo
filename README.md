# Ansible_demo

A safe Ansible project for checking that the GitHub MCP integration can read a
repository playbook and recognize a simulated DNS/package failure followed by
a missing-service failure.

## Files

- `ansible.cfg`: selects the project inventory.
- `inventory/hosts.ini`: maps `server01` to the local Ansible connection.
- `playbooks/site.yml`: uses deterministic `fail` tasks to simulate the sample
  log; it does not access the network, install packages, or manage services.
- `inventory/group_vars/all.yml`: example variable used by the playbook.

## Run locally

With Ansible installed, run from the project root. The playbook intentionally
finishes with a failure so the output can be used to test log diagnosis:

```powershell
ansible-playbook playbooks/site.yml
```

For the MCP demo, configure `REPO_OWNER = "mano42023"`,
`REPO_NAME = "Ansible_demo"`, and `PLAYBOOK_PATH = "playbooks/site.yml"` in
`main.py`. The MCP server reads from GitHub, so push these files to the
repository before running the integration.
