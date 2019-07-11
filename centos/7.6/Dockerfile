FROM centos:7.6.1810

# ------------------------------------------------------------------------------
# - Import the RPM GPG keys for repositories
# - Base install of required packages
# - Install supervisord (used to run more than a single process)
# - Install supervisor-stdout to allow output of services started by
#  supervisord to be easily inspected with "docker logs".
# ------------------------------------------------------------------------------
RUN rpm --rebuilddb \
	&& rpm --import \
		http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-7 \
	&& rpm --import \
		https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-7 \
	&& rpm --import \
		https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-GPG-KEY \
	&& yum -y install \
			--setopt=tsflags=nodocs \
			--disableplugin=fastestmirror \
		centos-release-scl \
		centos-release-scl-rh \
		epel-release \
		https://centos7.iuscommunity.org/ius-release.rpm \
	&& yum -y install \
			--setopt=tsflags=nodocs \
			--disableplugin=fastestmirror \
		inotify-tools-3.14-8.el7 \
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
		/var/log/supervisor/ \
	&& rm -rf /etc/ld.so.cache \
	&& rm -rf /sbin/sln \
	&& rm -rf /usr/{{lib,share}/locale,share/{man,doc,info,cracklib,i18n},{lib,lib64}/gconv,bin/localedef,sbin/build-locale-archive} \
	&& rm -rf /{root,tmp,var/cache/{ldconfig,yum}}/* \
	&& > /etc/sysconfig/i18n

# ------------------------------------------------------------------------------
# Provisioning
# - Networking
# - Configure SSH defaults for non-root public key authentication
# - Enable the wheel sudoers group
# ------------------------------------------------------------------------------

CMD ["/usr/bin/supervisord", "--configuration=/etc/supervisord.conf"] 
