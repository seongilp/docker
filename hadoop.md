

회사에서 Hadoop 사용할 일이 생겨서 집에있는 PC에 Ambari 구성했는데 자꾸 실패 ㅡㅡ..

HortonWorks 가이드대로 하면 되는데..

나중에 서버 구성할 때 메모리가 부족해서 어플리케이션이 제대로 올라오지 않는 문제가 발생하였음
```
10.25.1.210 master master.bigdata.com
10.25.1.211 slave01 slave01.bigdata.com
10.25.1.212 slave02 slave02.bigdata.com
```

vi /etc/yum.repos.d/CentOS-Base.repo
```
baseurl=http://centos.mirror.cdnetworks.com/$releasever/os/$basearch
baseurl=http://centos.mirror.cdnetworks.com/$releasever/updates/$basearch
baseurl=http://centos.mirror.cdnetworks.com/$releasever/extras/$basearch
gpgcheck=0
baseurl=http://centos.mirror.cdnetworks.com/$releasever/centosplus/$basearch
```

vi /etc/yum/pluginconf.d/fastestmirror.conf
```
enable=0
```

```
yum -y install ntp wget
systemctl is-enabled ntpd
systemctl enable ntpd
systemctl start ntpd
```

vi /etc/sysconfig/network
```
NETWORKING=yes
HOSTNAME=<fully.qualified.domain.name>
```

```
systemctl disable firewalld
service firewalld stop
setenforce 0
SELINUX=disabled in vi /etc/selinux/config
```

```
echo umask 0022 >> /etc/profile
```

```
wget -nv http://public-repo-1.hortonworks.com/ambari/centos7/2.x/updates/2.2.2.0/ambari.repo -O /etc/yum.repos.d/ambari.repo
yum -y install ambari-server
yum -y install ambari-agent
ssh-keygen -t dsa -P ” -f ~/.ssh/id_dsa
cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys
cat ~/.ssh/id_dsa.pub | ssh root@slave01 ‘cat >> ~/.ssh/authorized_keys’
cat ~/.ssh/id_dsa.pub | ssh root@slave02 ‘cat >> ~/.ssh/authorized_keys’
cat ~/.ssh/id_dsa.pub | ssh root@slave03 ‘cat >> ~/.ssh/authorized_keys’
```
