# deno-centos-build

A Vagrant box that should build deno.


## Getting Started

I run this on a beefy desktop with 8 cores and lots of RAM. Adjust the Vagrant
config to your specs. Be warned that building deno can take half an hour to
an hour, so be generous.

```bash
vi Vagrantfile   # make your adjustments to ram and cpus
```

Vagrant will download a centos7 vm image, install build dependencies, and clone
deno.

```
vagrant up
vagrant ssh
```

If all goes well, a **deno** directory will be sitting in **/home/vagrant**.
You're ready to build from source. Check the deno docs for the latest 
instructions.


