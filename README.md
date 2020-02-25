# Produzindo e consumindo mensagens usando Apache Kafka e Apache Avro


<p align="center">
    <a href="https://www.udemy.com/confluent-schema-registry/?couponCode=GITHUB">
        <img src="https://i.imgur.com/kHNTGv3.jpg" alt="Confluent Schema Registry and REST Proxy Course Logo"/>
    </a>
</p>

# Primeiros Passos
    1. Execute o comando "docker-compose up" para subir o container com o kafka cluster
        -HOST:  127.0.0.1 mude para 192.168.99.100 caso esteja usando o Docker Toolbox
        
        -Portas:
          - 2181:2181                 # Zookeeper
          - 3030:3030                 # Landoop UI
          - 8081-8083:8081-8083       # REST Proxy, Schema Registry, Kafka Connect ports
          - 9581-9585:9581-9585       # JMX Ports
          - 9092:9092                 # Kafka Broker
          
    2. Execute a interface gráfica para criar tópicos e Schemas: 127.0.0.1:3030 
    
    3. Ou crie Producers e Consumers via linha de comando;
        - Acessando linha de comando dentro do container, execute: 
            docker run --net=host -it confluentinc/cp-schema-registry:3.3.0 bash
            
        - Criando o Producer:     kafka-avro-console-producer \
                                 --broker-list 127.0.0.1:9092 --topic customer-avro \
                                 --property schema.registry.url=http://127.0.0.1:8081 \
                                 --property value.schema='{"type":"record","name":"myrecord","fields":[{"name":"f1","type":"string"}]}'  
        
        - Criando o Consumer:   kafka-avro-console-consumer --topic customer-avro \
                                --bootstrap-server 127.0.0.1:9092 \
                                --property schema.registry.url=http://127.0.0.1:8081 \
                                --from-beginning

# Conteúdo

 - Avro examples
 - Kafka Avro Producer & Consumer
 - Schema Evolutions
 
 # Documentação
  - https://kafka.apache.org/
  - https://avro.apache.org/
  - https://docs.confluent.io/current/schema-registry/schema_registry_tutorial.html
 
