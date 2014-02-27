# Base Vagrant box

FROM centos:6.4
MAINTAINER Cassiano Leal "cassianoleal@gmail.com"

# Create and configure vagrant user
RUN useradd --create-home -s /bin/bash vagrant
WORKDIR /home/vagrant

# Configure SSH access
RUN mkdir -p /home/vagrant/.ssh
RUN echo "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA6NF8iallvQVp22WDkTkyrtvp9eWW6A8YVr+kz4TjGYe7gHzIw+niNltGEFHzD8+v1I2YJ6oXevct1YeS0o9HZyN1Q9qgCgzUFtdOKLv6IedplqoPkcmF0aYet2PkEDo3MlTBckFXPITAMzF8dJSIFo9D8HfdOV0IAdx4O7PtixWKn5y2hMNG0zQPyUecp4pzC6kivAIhyfHilFR61RGL+GPXQ2MWZWFYbAGjyiYJnAmCP3NOTd0jMZEnDkbUvxhMmBYSdETk1rRgm+R4LOzFUGaHqHDLKLX+FIPKcF96hrucXzcWyLbIbEgE98OHlnVYCzRdK8jlqm8tehUc9c9WhQ== vagrant insecure public key" > /home/vagrant/.ssh/authorized_keys
RUN chown -R vagrant: /home/vagrant/.ssh
RUN echo -n 'vagrant:vagrant' | chpasswd

# Thanks to http://docs.docker.io/en/latest/examples/running_ssh_service/
RUN mkdir /var/run/sshd

# Update things and make sure the required packges are installed
RUN yum update -y && \
    yum install -y openssh-server sudo curl nfs-utils

# Enable passwordless sudo for the "vagrant" user
RUN echo 'vagrant ALL=NOPASSWD: ALL' > /etc/sudoers.d/vagrant

# # Puppet
# RUN wget http://apt.puppetlabs.com/puppetlabs-release-stable.deb -O /tmp/puppetlabs-release-stable.deb && \
#     dpkg -i /tmp/puppetlabs-release-stable.deb && \
#     apt-get update && \
#     apt-get install puppet puppet-common hiera facter virt-what -y --force-yes && \
#     rm -f /tmp/*.deb && \
#     apt-get clean

# # Chef
# RUN curl -L https://www.opscode.com/chef/install.sh -k | bash && apt-get clean
