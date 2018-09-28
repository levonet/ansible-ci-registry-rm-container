# CI: Remove docker container from registry

This role is useful in CI pipeline after closing Pull Request and removing infrastructure.

## Role Variables

- `ci_registry_scheme` (default: http)
- `ci_registry_url` (default: localhost): Registry API url.
- `ci_registry_container` (required): Container name.
- `ci_registry_tag` (required): Container tag.
- `ci_registry_username ` (optional): Registry username.
- `ci_registry_password` (optional): Registry password.

## Example Playbook

```yaml
- hosts: 127.0.0.1
  connection: local
  gather_facts: no
  vars:
    ci_registry_url: registry.myorg.com
    ci_registry_container: myorg/myapp
    ci_registry_tag: "{{ myapp_tag }}"
  roles:
  - role: levonet.registry-rm-container
```

And run in Jenkins:

```bash
ansible-playbook myplaybook.yml -e myapp_tag="${GIT_BRANCH}"
```

## License

[MIT](https://opensource.org/licenses/MIT)

## Author Information

This role was created by [Pavlo Bashynskyi](https://github.com/levonet)
