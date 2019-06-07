# amabri-blueprint

    1  sudo yum install update
    2  sudo yum install wget
    3  ls
    4  sudo wget -nv http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.1.2.1/ambari.repo -O /etc/yum.repos.d/ambari.repo
    5  cd /etc/yum.repos.d/
    6  ls
    7  cat /etc/yum.repos.d/ambari.repo
    8  yum -y install ambari-server ambari-agent
    9  sudo yum -y install ambari-server ambari-agent
   
   11  sudo ambari-server setup -s
   
   13  sudo chkconfig ambari-agent on
   14  sudo chkconfig ambari-server on
   15  sudo service ambari-server start
   16  sudo service ambari-agent start
   17  hostname
 

   21  sudo vi or nano  /etc/ambari-agent/conf/ambari-agent.ini
   22  hostname
       
Change the host name here

   25  cat /etc/ambari-agent/conf/ambari-agent.ini
 
   35  ls
   36  cd
   37  mkdir blueprint
   38  cd blueprint/
   39  ls
 
   42  sudo nano hostmapping.json
   
 
   
   47  sudo nano cluster_configuration.json
   48  hostname

curl -H "X-Requested-By: ambari" -X POST -u admin:admin http://yourhostname:8080/api/v1/blueprints/single-node-hdp-cluster -d  cluster_configuration.json

curl -H "X-Requested-By: ambari" -X POST -u admin:admin http://yourhostname:8080/api/v1/blueprint/my_bp_cluster -d @hostmapping.json


curl -H "X-Requested-By: ambari" -X GET -u admin:admin http://yourhostname:8080/api/v1/blueprint/my_bp_cluster/requests/
