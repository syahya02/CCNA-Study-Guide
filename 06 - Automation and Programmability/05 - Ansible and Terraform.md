# Ansible and Terraform

Both are common automation technologies, but with different workflows.

| Tool | Common model | Typical networking use |
|---|---|---|
| Ansible | Agentless playbooks; often imperative/declarative YAML tasks | Configure and validate Cisco devices |
| Terraform | Declarative desired-state infrastructure management | Provision cloud/network services through providers |

```yaml
# Illustrative Ansible structure (not a complete runnable playbook)
- name: Check device state
  hosts: routers
  gather_facts: false
  tasks:
    - name: Collect facts
      ansible.builtin.debug:
        msg: "Use a supported Cisco collection module here"
```

Understand *inventory, modules, playbooks* (Ansible) and *providers, resources, state, plan/apply* (Terraform). Keep credentials out of repositories; test changes in non-production environments first.

---
[← Previous: 04 - Lab - JSON and API Exercise](04%20-%20Lab%20-%20JSON%20and%20API%20Exercise.md) · [Next: 06 - AI and ML in Network Operations →](06%20-%20AI%20and%20ML%20in%20Network%20Operations.md)

[↑ Chapter study path](README.md) · [⌂ Main study guide](../README.md)
