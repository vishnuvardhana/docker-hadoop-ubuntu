#Apache Hadoop 2.8.1 Docker image

Forked: https://github.com/sequenceiq/docker-hadoop-ubuntu

Updated to Hadoop 2.8.1 and Java 8.

A few weeks ago we released an Apache Hadoop 2.3 Docker image (using CentOS 6.5 as the guest OS) - this quickly become the most [popular](https://registry.hub.docker.com/search?q=hadoop&s=downloads) Hadoop image in the Docker [registry](https://registry.hub.docker.com/).


Following the success of our CentOS based Hadoop 2.3 Docker [image](https://registry.hub.docker.com/u/sequenceiq/hadoop-docker/), the feedback and feature requests we received aligned with the Hadoop release cycle, so we have released an Apache Hadoop 2.6.0 Docker image on Ubuntu 14.04 as well - same as the previous version, it's available as a trusted and automated build on the official Docker [registry](https://registry.hub.docker.com/).


_FYI: All the former Hadoop releases (2.3, 2.4.0, 2.4.1, 2.5.0, 2.5.1, 2.5.2, 2.6.0) are available in the GitHub branches or our [Docker Registry](https://registry.hub.docker.com/u/sequenceiq/hadoop-ubuntu/) - check the tags._

# Build the image

If you'd like to try directly from the Dockerfile you can build the image as:

```
docker build  -t sequenceiq/hadoop-ubuntu:2.6.0 .
```
# Pull the image

The image is also released as an official Docker image from Docker's automated build repository - you can always pull or refer the image when launching containers.

```
docker pull sequenceiq/hadoop-ubuntu:2.6.0
```

# Start a container

In order to use the Docker image you have just build or pulled use:

```
docker run -i -t sequenceiq/hadoop-ubuntu:2.6.0 /etc/bootstrap.sh -bash
```

## Testing

You can run one of the stock examples:

```
cd $HADOOP_PREFIX
# run the mapreduce
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.6.0.jar grep input output 'dfs[a-z.]+'

# check the output
bin/hdfs dfs -cat output/*
```

## Hadoop native libraries, build, Bintray, etc

The Hadoop build process is no easy task - requires lots of libraries and their right version, protobuf, etc and takes some time - we have simplified all these, made the build and released a 64b version of Hadoop nativelibs on this [Bintray repo](https://bintray.com/sequenceiq/sequenceiq-bin/hadoop-native-64bit/2.5.0/view/files). Enjoy.

## Automate everything

As we have mentioned previously, a Docker file was created and released in the official [Docker repository](https://registry.hub.docker.com/u/sequenceiq/hadoop-ubuntu/)
