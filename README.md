# Ansible_demo

A minimal, safe Ansible project for checking that the GitHub MCP integration can
read a repository playbook.

## Files

- `ansible.cfg`: selects the project inventory.
- `inventory/hosts.ini`: targets localhost only.
- `playbooks/site.yml`: debug-only playbook; it makes no system changes.
- `inventory/group_vars/all.yml`: example variable used by the playbook.

## Run locally

With Ansible installed, run from the project root:

```powershell
ansible-playbook playbooks/site.yml
```

For the MCP demo, configure `REPO_OWNER = "mano42023"`,
`REPO_NAME = "Ansible_demo"`, and `PLAYBOOK_PATH = "playbooks/site.yml"` in
`main.py`. The MCP server reads from GitHub, so push these files to the
repository before running the integration.
