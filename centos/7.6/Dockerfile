FROM centos:7
#FROM centos:7.6.1810
# 安装基础软件
RUN yum clean all &&\
	yum install setuptools -y

COPY meld3-1.0.2 /root/meld3-1.0.2
WORKDIR /root/meld3-1.0.2 
RUN mkdir /etc/supervisord.d
COPY sshd.conf /etc/supervisord.d/
RUN python setup.py install
COPY supervisor-4.0.3 /root/supervisor-4.0.3
WORKDIR /root/supervisor-4.0.3 
RUN python setup.py install
COPY supervisord.conf /etc/supervisord.conf
CMD ["supervisord"]
