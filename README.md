# setup-lxd

*NB: this action is currently in alpha, breaking changes can occur at any time.
Please pin a SHA or exact version in your CI.*

A GitHub Action which installs and configures the LXD snap on a runner.

When run with no inputs:
```yaml
uses: canonical/setup-lxd
```
this action will use the LXD snap pre-installed on the runner. If LXD is not
installed, it will `sudo snap install lxd` from the default channel.

You can specify a snap channel with the `channel` input:
```yaml
uses: canonical/setup-lxd
with:
  channel: 5.2/candidate
```
and then this action will install/refresh LXD from the specified channel.

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
        channel: latest/stable  # switch from distro's LTS channel to latest/stable

    - name: Launch container
      run: |
        lxc launch ubuntu:22.04 u1
```

```yaml
name: "Configure pre-installed LXD"
on: push
jobs:
  job1:
    runs-on: ubuntu-22.04
    steps:

    - name: Setup LXD
      uses: canonical/setup-lxd@[version]
      # uses pre-installed LXD snap (22.04 comes with 5.0/stable)

    - name: Launch container
      run: |
        lxc launch ubuntu:22.04 u1
```

## Maintainers

- [barrettj12](https://github.com/barrettj12)
