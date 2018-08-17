## Ubuntu install 


$ sudo apt-get update  
$ sudo apt-get upgrade   
  
> Java Install  
리포지토리 등록 시 메세지, 다음을 설치한다. [sudo: add-apt-repository: command not found]     
$ sudo apt-get install python-software-properties  
$ sudo apt-get install software-properties-common    

> 리포지토리 등록  
$ sudo add-apt-repository ppa:webupd8team/java  
$ apt-get install oracle-java8-installer    
$ java -version    
  
$ apt-get install openssl-server  

> Root 계정이 아닌 일반 계정 hduser 로 hadoop 실행하기  
$ sudo addgroup hadoop  
$ sudo adduser --ingroup hadoop hduser  // 암호입력 나머진 enter   
$ sudo vim /etc/sudoers  ( root 설정 밑에 hduser 설정 추가 )  
root ALL(ALL:ALL) ALL   
hduser ALL(ALL:ALL) ALL    
  
<pre>
<code>
$ vim ~/.bashrc  // 다음을 등록해 줌.

# HADOOP 
export JAVA_HOME=/usr/lib/jvm/java-8-oracle
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$HADOOP_HOME/bin
export PATH=$PATH:$HADOOP_HOME/sbin
export PATH=$PATH:$JAVA_HOME/bin
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HODOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
export PATH=$PATH:/usr/local/hadoop/bin/
</code>
</pre>

<pre>
<code>
$ sudo su hduser  

1) Generate ssh key without password  
$ ssh-keygen -t rsa -P ""  
  
2) Copy id_rsa.pub to authorized-keys  
$  cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys  
  
3) Start ssh localhost  
$ ssh localhost  
  
4) now go to the hadoop sbin directory and start hadoop  
$./start-all.sh   
./start-all.sh  
This script is Deprecated. Instead use start-dfs.sh and start-yarn.sh
Starting namenodes on [localhost]
localhost: starting namenode, logging to /home/amtex/Documents/installed/hadoop/logs/hadoop-amtex-namenode-amtex-desktop.out
localhost: starting datanode, logging to /home/amtex/Documents/installed/hadoop/logs/hadoop-amtex-datanode-amtex-desktop.out
Starting secondary namenodes [0.0.0.0]
0.0.0.0: starting secondarynamenode, logging to /home/amtex/Documents/installed/hadoop/logs/hadoop-amtex-secondarynamenode-amtex-desktop.out
starting yarn daemons
starting resourcemanager, logging to /home/amtex/Documents/installed/hadoop/logs/yarn-amtex-resourcemanager-amtex-desktop.out
localhost: starting nodemanager, logging to /home/amtex/Documents/installed/hadoop/logs/yarn-amtex-nodemanager-amtex-desktop.out
  
  
5) password not asking   
$ jps   
12373 Jps  
11823 SecondaryNameNode  
11643 DataNode  
12278 NodeManager  
11974 ResourceManager  
11499 NameNode

</code>
</pre>

참조 :  
 http://coding-factory.tistory.com/60  
 https://www.joinc.co.kr/w/man/12/hadoop/install  
 
