## **Debian installation:**


**Prerequisites:**

     $ sudo apt update && sudo apt upgrade

     $ sudo apt install apt-transport-https openjdk-8-jre-headless uuid runtime pwgen


**Next install MongoDB:**

     $ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5

     $ echo "deb http://repo.mongodb.org/apt/debian stretch/mongodb-org/3.6 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list

     $ sudo apt-get update

     $ sudo apt-get install -y mongodb-org



**To enable MongoDB during OS system startup and verify its running:**

     $ sudo systemctl daemon-reload

     $ sudo systemctl enable mongod.service

     $ sudo systemctl restart mongod.service



**Install Elasticsearch:**

     $ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

     $ echo "deb https://artifacts.elastic.co/packages/5.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-5.x.list

     $ sudo apt update && sudo apt install elasticsearch


**Modify the Elasticsearch configuration file (/etc/elasticsearch/elasticsearch.yml) and set the cluster name to graylog and uncomment (remove the # as first character) the line:**

	cluster.name: graylog

**After you have modified the configuration, you can start Elasticsearch and verify it is running:**

     $ sudo systemctl daemon-reload

     $ sudo systemctl enable elasticsearch.service

     $ sudo systemctl restart elasticsearch.service



**Install GrayLog:**

     $ wget https://packages.graylog2.org/repo/packages/graylog-2.4-repository_latest.deb

     $ sudo dpkg -i graylog-2.4-repository_latest.deb

     $ sudo apt update && sudo apt install graylog-server


**Edit the Configuration File**

**Read the instructions within the configurations file and edit as needed, located at /etc/graylog/server/server.conf. Additionally add password_secret and root_password_sha2 as these are mandatory and Graylog will not start without them.**

**To create your root_password_sha2 run the following command**

	echo -n "Enter Password: " && head -1 </dev/stdin | tr -d '\n' | sha256sum | cut -d" " -f1

**The last step is to enable Graylog during the operating system’s startup and verify it is running.**

     $ sudo systemctl daemon-reload

     $ sudo systemctl enable graylog-server.service

     $ sudo systemctl start graylog-server.service
