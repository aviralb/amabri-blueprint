sudo yum install update
sudo yum install wget
ls
sudo wget -nv http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.1.2.1/ambari.repo -O /etc/yum.repos.d/ambari.repo
cd /etc/yum.repos.d/
ls
cat /etc/yum.repos.d/ambari.repo
yum -y install ambari-server ambari-agent
sudo yum -y install ambari-server ambari-agent
   
sudo ambari-server setup -s
   
sudo chkconfig ambari-agent on
sudo chkconfig ambari-server on
sudo service ambari-server start
sudo service ambari-agent start
hostname
 

sudo vi or nano  /etc/ambari-agent/conf/ambari-agent.ini
hostname
       
Change the host name here

 cat /etc/ambari-agent/conf/ambari-agent.ini
 
ls
cd
mkdir blueprint
cd blueprint/
ls
 
sudo nano hostmapping.json
   
 
   
sudo nano cluster_configuration.json
hostname

curl -H "X-Requested-By: ambari" -X POST -u admin:admin http://yourhostname:8080/api/v1/blueprints/single-node-hdp-cluster -d  cluster_configuration.json

curl -H "X-Requested-By: ambari" -X POST -u admin:admin http://yourhostname:8080/api/v1/blueprint/my_bp_cluster -d @hostmapping.json


curl -H "X-Requested-By: ambari" -X GET -u admin:admin http://yourhostname:8080/api/v1/blueprint/my_bp_cluster/requests/
