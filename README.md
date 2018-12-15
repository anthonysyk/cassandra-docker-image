# cassandra-docker-image

### Single Node Cassandra

Based Image used: official 3.11 cassandra image 

Build image
```bash
docker build -t versatile/cassandra:latest cassandra-single-node/.
```

Run container with port mapping for external connexion 
```bash
docker run -v /data/cassandra:/var/lib/cassandra -d -p 9042:9042 -p 9160:9160 --name cassandra versatile/cassandra
```

### Additional informations

- 7000 : intra-node communication
- 7001 : TLS inrra-node communication
- 7199 : JMX
- 9042 : CQL
- 9160 : thrift service
