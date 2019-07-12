FROM registry.cn-beijing.aliyuncs.com/hobbits/ubuntu:18.04
RUN apt-get update && apt-get install -y --no-install-recommends \
		bzip2 \
		unzip \
		xz-utils \
                sudo \
		ca-certificates 


# Default to UTF-8 file.encoding
ENV LANG C.UTF-8

# add a simple script that can auto-detect the appropriate JAVA_HOME value
# based on whether the JDK or only the JRE is installed

RUN add-apt-repository ppa:openjdk-r/ppa \
	&& apt-get update \
	&& apt-get install -y openjdk-8-jdk \
	&& apt-get install ca-certificates-java \
	&& update-ca-certificates -f

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
