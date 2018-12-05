FROM anapsix/alpine-java:8

# Install sbt
ENV SBT_VERSION 0.13.17
ENV SCALA_VERSION 2.11.7
ENV PATH $PATH:/root/sbt/bin
RUN apk add --no-cache curl=7.61.1-r1 && \
  curl -fsL https://piccolo.link/sbt-$SBT_VERSION.tgz | gunzip -dc | tar xf - -C /root && \
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
