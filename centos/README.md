# CentOS 6.5 base box

This folder contains an example of a Dockerfile that builds an image ready for
usage with Vagrant. Please check out the [source](centos/Dockerfile)
for more information on building your own.

To turn this into a box:

```
docker build -t cassianoleal/vagrant-centos:6.5_nocm .
docker push cassianoleal/vagrant-centos
tar cvzf centos65_nocm.box ./metadata.json ./Vagrantfile
```

This box works by using Vagrant's built-in `Vagrantfile` merging to setup defaults
for Docker. These defaults can easily be overwritten by higher-level Vagrantfiles
(such as project root Vagrantfiles).
