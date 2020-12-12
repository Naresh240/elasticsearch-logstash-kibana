# elasticsearch-logstash-kibana

# Elastic search SetUp
    wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.9.3-x86_64.rpm
    rpm -ivh elasticsearch-7.9.3-x86_64.rpm
  Open "elasticsearch.yml" and edit below details
    
    vi /etc/elasticsearch/elasticsearch.yml
    --------------------------------------------------
      network.host: 0.0.0.0
      http.port: 9200
      discovery.type: single-node
      xpack.security.enabled: true
      xpack.security.transport.ssl.enabled: true
    --------------------------------------------------
  View the logs:
      
    vi /var/log/elasticsearch/elasticsearch.log
  Start the service
      
    service elasticsearch start
  Check status of Elastic Search
      
    service elasticsearch status
  Set Built-in Account Passwords:
    
    cd /usr/share/elasticsearch
    ./bin/elasticsearch-setup-passwords interactive
  Check elasticsearch in UI: Allow port=9200 in security group
    <IP-Adress>:9200

  ![image](https://user-images.githubusercontent.com/58024415/101988319-df230880-3cbe-11eb-8e92-070301761be0.png)

Provide username and password:

  ![image](https://user-images.githubusercontent.com/58024415/101988340-f95ce680-3cbe-11eb-95bc-738dbac72e7e.png)

# Kibana SetUp
    wget https://artifacts.elastic.co/downloads/kibana/kibana-7.9.3-x86_64.rpm
    rpm -ivh kibana-7.9.3-x86_64.rpm
  Open "kibana.yml" and edit below details
      
    vi /etc/kibana/kibana.yml
    --------------------------------------------------
      server.port: 5601
      server.host: "0.0.0.0"
      elasticsearch.hosts: ["http://localhost:9200"]
      elasticsearch.username: "kibana_system"
      elasticsearch.password: "test123"
    --------------------------------------------------
  Start the service
      
    service kibana start

  Check status of Elastic Search
      
    service kibana status
  Check Kibana in UI: Allow port=5601 in security group
      <IP-Adress>:5601
   
  ![image](https://user-images.githubusercontent.com/58024415/101988304-c87cb180-3cbe-11eb-905e-59844135aa9c.png)
  
  provide elastic search username and password:
   
  ![image](https://user-images.githubusercontent.com/58024415/101988374-32955680-3cbf-11eb-97b2-ea31bb01bffc.png)
