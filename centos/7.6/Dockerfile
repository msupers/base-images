FROM centos:7.6.1810

# ------------------------------------------------------------------------------
# - Import the RPM GPG keys for repositories
# - Base install of required packages
# - Install supervisord (used to run more than a single process)
# - Install supervisor-stdout to allow output of services started by
#  supervisord to be easily inspected with "docker logs".
# ------------------------------------------------------------------------------
RUN  yum -y install \
                epel-release \
		openssh-clients-7.4p1-16.el7 \
		openssh-server-7.4p1-16.el7 \
		openssl-1.0.2k-16.el7 \
		python-setuptools-0.9.8-7.el7 \
		sudo-1.8.23-3.el7 \
		yum-plugin-versionlock-1.1.31-50.el7 \
	&& yum versionlock add \
		inotify-tools \
		openssh \
		openssh-server \
		openssh-clients \
		python-setuptools \
		sudo \
		yum-plugin-versionlock \
	&& yum clean all \
	&& easy_install \
		'supervisor == 4.0.3' \
		'supervisor-stdout == 0.1.1' \
	&& mkdir -p \
		/var/log/supervisor/  
COPY ./supervisord.conf /etc/
# ------------------------------------------------------------------------------
# Provisioning
# - Networking
# - Configure SSH defaults for non-root public key authentication
# - Enable the wheel sudoers group
# ------------------------------------------------------------------------------

CMD ["/usr/bin/supervisord", "--configuration=/etc/supervisord.conf"] 
