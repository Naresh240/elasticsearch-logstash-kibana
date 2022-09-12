# elasticsearch-logstash-kibana

![image](https://user-images.githubusercontent.com/58024415/126860115-982ced35-0a2e-4daf-b21a-3aafca404059.png)

## ELK search SetUp

Get GPG Key and Repo file from [link](https://www.elastic.co/guide/en/elasticsearch/reference/current/rpm.html)

Import the Elasticsearch GPG Key:
```bash
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch
```

Create Repo file at ```/etc/elasticsearch``` with the name of ```elasticsearch.repo``` with belo content

```bash
[elasticsearch]
name=Elasticsearch repository for 8.x packages
baseurl=https://artifacts.elastic.co/packages/8.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md
```

Install Elasticsearch, Logstash and Kibana

```bash
yum install elasticsearch logstash kibana -y
```
   
If you want to see elastic search in UI, need to edit ```elasticsearch.yml``` shown as below
    
    
```bash    
vi /etc/elasticsearch/elasticsearch.yml
--------------------------------------------------
network.host: 0.0.0.0
http.port: 9200
xpack.security.enabled: true         #also need to modify xpack.security.enabled as false
---------------------------------------------------
```

Start elasticsearch service

```bash      
service elasticsearch start
```

Check status of Elastic Search

```bash
service elasticsearch status
```

Check elasticsearch in UI: Allow port=9200 in security group
    <IP-Adress>:9200
  
  ![image](https://user-images.githubusercontent.com/58024415/189602780-add232b6-49e2-4556-af5b-55f303f52e9e.png)

# Kibana SetUp
Open "kibana.yml" and edit below details

```bash
vi /etc/kibana/kibana.yml
-------------------------------------------------
server.port: 5601
server.host: "0.0.0.0"
elasticsearch.hosts: ["http://localhost:9200"]
-------------------------------------------------
```

Start kibana service

```bash
service kibana start
```

Check status of kibana

```bash
service kibana status
```

Check Kibana in UI: Allow port=5601 in security group
  <IP-Adress>:5601

![image](https://user-images.githubusercontent.com/58024415/101978000-bdeaf980-3c77-11eb-8ddc-6ea7b9d518b1.png)

## Clone application and send logs to Elasticsearch

Create log file with below commands
```bash
cd springboot-elk

Run application for logs:
   
mvn spring-boot:run
  
Check log file at /root/logback
```

Run logstash command to send logs to elasticsearch

```bash
cp logback.conf /usr/share/logstash/logback.conf        # copy logback configuration file
/usr/share/logstash/bin/logstash -f logback.conf        # sending logs to elastic search
```

![image](https://user-images.githubusercontent.com/58024415/189606162-a2c65ca7-6e25-431e-8d5b-67b76af42658.png)

Click on ```dashboard```

![image](https://user-images.githubusercontent.com/58024415/189606282-c694666f-5ff4-4c70-b350-d8724d42aac5.png)

Click on ```create new view```

![image](https://user-images.githubusercontent.com/58024415/189606575-a3f62764-3f66-449c-8b90-808d223dab08.png)

Click on ```save data view to kibana```

![image](https://user-images.githubusercontent.com/58024415/189606848-59a15b0c-80bf-48dc-8339-f9a85364c737.png)

Click on ```discover``` and see logs
