# Apache ZooKeeper [![GitHub Actions CI][ciBadge]][ciLink] [![Travis CI][trBadge]][trLink] [![Maven Central][mcBadge]][mcLink] [![License][liBadge]][liLink]

<p align="left">
  <a href="https://zookeeper.apache.org/">
    <img src="https://zookeeper.apache.org/images/zookeeper_small.gif"" alt="https://zookeeper.apache.org/"><br/>
  </a>
</p>

For the latest information about Apache ZooKeeper, please visit our website at:

   https://zookeeper.apache.org

and our wiki, at:

   https://cwiki.apache.org/confluence/display/ZOOKEEPER

## Packaging/release artifacts

Either downloaded from https://zookeeper.apache.org/releases.html or
found in zookeeper-assembly/target directory after building the project with maven.

    apache-zookeeper-[version].tar.gz

        Contains all the source files which can be built by running:
        mvn clean install

        To generate an aggregated apidocs for zookeeper-server and zookeeper-jute:
        mvn javadoc:aggregate
        (generated files will be at target/site/apidocs)

    apache-zookeeper-[version]-bin.tar.gz

        Contains all the jar files required to run ZooKeeper
        Full documentation can also be found in the docs folder

As of version 3.5.5, the parent, zookeeper and zookeeper-jute artifacts
are deployed to the central repository after the release
is voted on and approved by the Apache ZooKeeper PMC:

  https://repo1.maven.org/maven2/org/apache/zookeeper/zookeeper

## Java 8

If you are going to compile with Java 1.8, you should use a
recent release at u211 or above.

# Contributing
We always welcome new contributors to the project! See [How to Contribute](https://cwiki.apache.org/confluence/display/ZOOKEEPER/HowToContribute) for details on how to submit patches as pull requests and other aspects of our contribution workflow.


[ciBadge]: https://github.com/apache/zookeeper/workflows/CI/badge.svg
[ciLink]: https://github.com/apache/zookeeper/actions
[liBadge]: https://img.shields.io/github/license/apache/zookeeper?color=282661
[liLink]: https://github.com/apache/zookeeper/blob/master/LICENSE.txt
[mcBadge]: https://img.shields.io/maven-central/v/org.apache.zookeeper/zookeeper
[mcLink]: https://zookeeper.apache.org/releases
[trBadge]: https://travis-ci.org/apache/zookeeper.svg?branch=master
[trLink]: https://travis-ci.org/apache/zookeeper
# 部署步骤
````
vim conf/zoo.cfg 
修改为真实服务器ip
server.1=xxx.1 :2888:3888
server.2=xxx.2:2888:3888
server.3=xxx.3:2888:3888
保存退出
在各自对应的服务目录中运行
mkdir -p data
#server1服务器中
echo 1 > data/myid
#server2服务器中
echo 2 > data/myid
#server3服务器中
echo 3 > data/myid

在各自服务器 中运行 bin/zkServer.sh start 
bin/zkServer.sh status 查看运行状态
出现以下内容为成功
ZooKeeper JMX enabled by default
Using config: /usr/local/cluster-zookeeper/bin/../conf/zoo.cfg
Client port found: 2181. Client address: localhost. Client SSL: false.
Mode: leader

