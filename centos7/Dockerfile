FROM centos:7.9.2009


WORKDIR /programs


## CentOS 8.x has not been supported in 2021. All URL of the repositories are transferred to
## the URL: vault.centos.org. Before stating installing the repository, the commands below shall be executed.

RUN cd /etc/yum.repos.d/  && \
	sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* && \
	sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*



# OpenSSL-devel is necessary because the later installation of cmake 4.x version
# epel-release package is for jq.
# libnl3-devel libnl3-cli is the necessary package when compiling the project; on the CENTOS 7 the packages are old.
RUN yum install -y git gcc gcc-c++ glibc-devel make cmake libstdc++-devel sudo unzip rsync wget openssl-devel epel-release && \
	yum install -y jq && \
	yum groupinstall -y "Development Tools" && \
	sudo yum install epel-release -y && \
	sudo yum install -y libnl3-devel libnl3-cli 

# Installing cmake 4.x (project necessary)
RUN cd /opt && wget https://github.com/Kitware/CMake/releases/download/v4.1.2/cmake-4.1.2.tar.gz && \
	tar zxvf cmake-4.1.2.tar.gz && cd cmake-4.1.2 && ./bootstrap --prefix=/usr/local && make && sudo make install

# RUN yum install libpcap && \
# 	yum -y --enablerepo=powertools install libpcap-devel