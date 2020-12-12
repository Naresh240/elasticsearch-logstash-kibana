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
    --------------------------------------------------
  
  Start the service
      
    service elasticsearch start

  Check status of Elastic Search
      
    service elasticsearch status
  Check elasticsearch in UI: Allow port=9200 in security group
    <IP-Adress>:9200
  
  ![image](https://user-images.githubusercontent.com/58024415/101978019-deb34f00-3c77-11eb-8f00-a7dc5b8d16e6.png)

# Kibana SetUp
    wget https://artifacts.elastic.co/downloads/kibana/kibana-7.9.3-x86_64.rpm
    rpm -ivh kibana-7.9.3-x86_64.rpm
  Open "kibana.yml" and edit below details
      
    vi /etc/kibana/kibana.yml
    --------------------------------------------------
      server.port: 5601
      server.host: "0.0.0.0"
      elasticsearch.hosts: ["http://localhost:9200"]
    --------------------------------------------------
  Start the service
      
    service kibana start

  Check status of Elastic Search
      
    service kibana status
  Check Kibana in UI: Allow port=5601 in security group
      <IP-Adress>:5601
  
  ![image](https://user-images.githubusercontent.com/58024415/101978000-bdeaf980-3c77-11eb-8ddc-6ea7b9d518b1.png)
