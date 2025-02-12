# setup-lxd

*NB: this action is currently in alpha, breaking changes can occur at any time.
Please pin a SHA or exact version in your CI.*

A GitHub Action which installs and configures the LXD snap on a runner.

When run with no inputs:
```yaml
uses: canonical/setup-lxd@main
```
this action will install or refresh the LXD snap using the `latest/candidate` channel.

You can specify a different `group` membership required to access LXD:
```yaml
uses: canonical/setup-lxd@main
with:
  group: lxd
```
and then users of that group will have full control over LXD.

You can specify a snap channel with the `channel` input:
```yaml
uses: canonical/setup-lxd@main
with:
  channel: 5.21/stable
```
and then this action will install/refresh LXD from the specified channel.

If you require more control over LXD's initalisation, you can also specify the
preseed input:
```yaml
uses: canonical/setup-lxd@main
with:
  preseed: |
    config:
      core.https_address: 192.0.2.1:9999
      images.auto_update_interval: 15
    networks:
    - name: lxdbr0
      type: bridge
      config:
        ipv4.address: auto
        ipv6.address: none
```
See the [Initialise LXD documentation](https://documentation.ubuntu.com/lxd/en/latest/howto/initialize/#non-interactive-configuration)
for more information.

## Example usage

```yaml
name: "Install latest LXD"
on: push
jobs:
  job1:
    runs-on: ubuntu-latest
    steps:

    - name: Setup LXD
      uses: canonical/setup-lxd@[version]
      with:
        channel: latest/edge

    - name: Launch container
      run: |
        lxc launch ubuntu:24.04 u1
```

## Maintainers

- [Simon Deziel](https://github.com/simondeziel/)
- [Tom Parrott](https://github.com/tomponline/)
