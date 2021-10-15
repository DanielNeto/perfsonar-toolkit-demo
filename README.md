# perfsonar-toolkit-demo

## VM specs

| Spec | Value |
| --- | --- |
| OS | CentOS 7 |
| CPU | 2 vCPUs |
| RAM | 4096 MB |

## Pre-Installation

1. Clone code
```bash
yum install git -y
git clone https://github.com/DanielNeto/perfsonar-toolkit-demo.git
cd perfsonar-toolkit-demo
```

2. Copy external repos
```bash
cp elastic.repo /etc/yum.repos.d/elastic.repo
cp opendistro.repo /etc/yum.repos.d/opendistro.repo
```

3. Add perfSONAR repo
```bash
yum install epel-release -y
yum install http://software.internet2.edu/rpms/el7/x86_64/latest/packages/perfSONAR-repo-0.10-1.noarch.rpm -y
yum update -y
```

## Installation

1. Elmond
```bash
yum install elmond/python3-dateutil-2.6.1-6.el7.noarch.rpm -y
yum install elmond/python3-elasticsearch-7.0.5-2.el7.noarch.rpm -y
yum install elmond/perfsonar-elmond-4.4.0-0.0.a1.el7.noarch.rpm -y
```

2. Logstash
```bash
yum install logstash/perfsonar-logstash-4.4.0-0.0.a1.el7.noarch.rpm -y
```

3. Archive
```bash
yum install archive/perfsonar-archive-4.4.0-0.0.a1.el7.noarch.rpm -y
```

4. Core + Testpoint
```bash
yum install toolkit/perfsonar-toolkit-install-4.4.0-1.el7.noarch.rpm -y
yum install core/perfsonar-core-4.4.0-1.el7.noarch.rpm -y
```

5. Toolkit
```bash
yum install toolkit/perfsonar-toolkit-servicewatcher-4.4.0-1.el7.noarch.rpm -y
yum install toolkit/perfsonar-toolkit-systemenv-4.4.0-1.el7.noarch.rpm -y
yum install toolkit/perfsonar-toolkit-4.4.0-1.el7.noarch.rpm -y
```

## Kibana (optional)

1. Install
```bash
yum install archive/kibana-archive-4.4.0-0.0.a1.el7.noarch.rpm -y
```

2. Run kibana on all IPs
```bash
echo "server.host: 0.0.0.0" >> /etc/kibana/kibana.yml && systemctl restart kibana
iptables -A IN_public_allow -p tcp --dport 5601 -j ACCEPT
```