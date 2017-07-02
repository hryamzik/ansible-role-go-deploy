# go-deploy

This role is designed to build and deploy go binaries.

## Dependencies

go_build_required_packages:
  - github.com/elazarl/go-bindata-assetfs/...
  - github.com/jteeuwen/go-bindata/...
  - github.com/GeertJohan/go.rice
  - github.com/GeertJohan/go.rice/rice

## Subprojects

If repository has multiple project directories inside they can be defined with `go_build_subprojects` variable.

## Handlers

`go_deploy_notify` accepts list of handlers.

## Supported architectures

Checkout [vars](/hryamzik/ansible-role-go-deploy/vars/main.yml), more could be added.

## Limitations

Role builds binaries only once for hosts in play so it may be a problem if they are of different architectures.

## Examples

```yml
- hosts: pi
  become: yes
  roles:
    - role: go-deploy
      go_build_repo: github.com/inCaller/prometheus_bot
      go_deploy_notify:
        - prometheus_bot reload
```

Note that service is defined outside this role.
