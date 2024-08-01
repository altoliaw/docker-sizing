FROM centos:centos8.4.2105


WORKDIR /programs


## CentOS 8.x has not been supported in 2021. All URL of the repositories are transferred to
## the URL: vault.centos.org. Before stating installing the repository, the commands below shall be executed.

RUN cd /etc/yum.repos.d/  && \
	sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* && \
	sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*


# RUN yum install -y git gcc gcc-c++ glibc-devel make cmake libstdc++-devel && \
# 	yum groupinstall -y "Development Tools"