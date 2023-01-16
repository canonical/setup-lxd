# setup-lxd

A GitHub Action which installs and configures the LXD snap on a runner.

It will default install LXD from the `latest/stable` snap channel. You can specify a different channel using the `channel` input. (See `snap info lxd` for a list of available channels).

The action will also refresh LXD if it is already installed on a runner,
it can be skipped using the option 'refresh: false'.

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
        refresh: false

    - name: Launch container
      run: |
        lxc launch ubuntu:22.04 u1
```

## Maintainers

- [barrettj12](https://github.com/barrettj12)
