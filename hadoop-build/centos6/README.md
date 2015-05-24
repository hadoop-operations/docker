# Hadoop Operations - CentOS 6 Hadoop Build Env

A docker container, based on `centos:centos6`, that contains everything
necessary to build Hadoop 2.6.0.

## Usage

Start an interactive container with a local Hadoop source code directory
mounted within the container. This example assumes the Hadoop 2.6.0 source
is unpacked in the current working directory.

```sh
$ docker run -it -v `pwd`/hadoop-2.6.0-src:/hadoop-src  hadoop-operations:hadoop-build
```

Build Hadoop from within the container. Since the source directory is mounted
from the container's host, the result of the build will be accessible from
outside the container.

```sh
$ cd /hadoop-src
$ /apache-maven-3.3.3/bin/mvn -Pdist -Pnative -Dtar -DskipTests package
```

The final distribution tarball can be found in `hadoop-dist/target/hadoop-2.6.0.tar.gz`.
