FROM ubuntu:18.04
RUN apt-get update && apt-get install python python-setuptools vim net-tools ca-certificates curl git gcc make openssl libssl-dev iptables  -y
COPY meld3-1.0.2 /root/meld3-1.0.2
WORKDIR /root/meld3-1.0.2 
RUN mkdir /etc/supervisord.d
RUN python setup.py install
COPY supervisor-4.0.3 /root/supervisor-4.0.3
WORKDIR /root/supervisor-4.0.3 
RUN python setup.py install
COPY supervisord.conf /etc/supervisord.conf
CMD ["supervisord"]
