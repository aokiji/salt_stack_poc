# Salt PoC

Provision a virtual machine using salt in masterless setup.

## Getting started

Just fire up vagrant

```
vagrant up
```

This will create the virtual machine and provision it.

If you make changes to the provisioning and wish to redo it, then

```
vagrant provision
```

## Setup

in provision/salt are the recipies executed on the minions, place there your configuration.

for example for installing vim you would include in your top.sls file

```yaml
# provision/salt/top.sls
base:
  '*':
    - vim
```

And setup a vim recipe

```yaml
# provision/salt/vim.sls
vim-enhanced:
  pkg.installed
```

## Advice

To run salt on the local machine, ssh to it and run

```
salt-call --local state.apply
```

This in general is faster than vagrant provision and you could either just run one of the states instead of running the whole thing.

For debug info run with debug flag

```
salt-call --local state.apply -l debug
```
