# setup-lxd

A GitHub Action which installs and configures the LXD snap on a runner.

By default, this action will install LXD from the `latest/stable` snap channel. You can specify a different channel using the `channel` input. (See `snap info lxd` for a list of available channels).

## Example usage

```yaml
name: "Example"
on: push
jobs:
  job1:
    runs-on: ubuntu-latest
    steps:

    - name: Setup LXD
      uses: canonical/setup-lxd@[sha]
      with:
        channel: 5.0/stable

    - name: Launch container
      run: |
        lxc launch ubuntu:22.04 u1
```

## Maintainers

- [barrettj12](https://github.com/barrettj12)