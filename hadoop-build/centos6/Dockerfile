FROM centos:centos6

MAINTAINER E. Sammer <esammer@gmail.com>
LABEL Description="Full Hadoop 2.6.0 build environment for CentOS 6.x" Version="2.0.0"

ADD jdk-7u80-linux-x64.rpm /

RUN yum update -y && yum clean all
RUN yum install -y epel-release gcc gcc-c++ autoconf automake make snappy snappy-devel tar gzip bzip2 libtool cmake which zlib-devel openssl-devel
RUN curl -L -O https://github.com/google/protobuf/archive/v2.5.0.tar.gz && tar -zxvf v2.5.0.tar.gz
RUN cd protobuf-2.5.0 && ./autogen.sh && ./configure && make install && cd ../ && rm -rf protobuf-2.5.0 v2.5.0.tar.gz
RUN curl -L -O http://mirror.symnds.com/software/Apache/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz && tar -zxvf apache-maven-3.3.3-bin.tar.gz && rm -rf apache-maven-3.3.3-bin.tar.gz
RUN rpm -ihv /jdk-7u80-linux-x64.rpm && rm jdk-7u80-linux-x64.rpm

CMD ["/bin/bash"]
