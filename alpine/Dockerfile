FROM anapsix/alpine-java:latest

# Install sbt
ENV SBT_VERSION 0.13.15
ENV SCALA_VERSION 2.12.2
ENV PATH $PATH:/root/sbt/bin
RUN apk add --no-cache curl=7.61.1-r0 && \
  curl -fsL http://dl.bintray.com/sbt/native-packages/sbt/$SBT_VERSION/sbt-$SBT_VERSION.tgz | gunzip -dc | tar xf - -C /root && \
  apk del curl

# Create project and compile to resolve sbt and scala dependencies
RUN mkdir -p /opt/app/src/main/scala
WORKDIR /opt/app
RUN \
  echo -e 'package com.better\nobject A {}' > /opt/app/src/main/scala/package.scala && \
  echo -e 'organization := "com.better"\nscalaVersion := "'$SCALA_VERSION'"' > /opt/app/build.sbt && \
  sbt compile
WORKDIR /opt
RUN rm -r /opt/app
