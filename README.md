# cassandra-docker-image

### Single Node Cassandra

Based Image used: official 3.11 cassandra image 

### Setup Custom Superuser (Before building you image)
* update file cassandra-single-node/scripts/2-create-new-user.sql with your superuser name and password
* you can also update the default superuser password on cassandra-single-node/scripts/3-remove-default-user.sql
* finally you can run this command **once your container is running**
```
docker exec -d cassandra sh /home/setup/setup-superuser.sh
```

### Build your image

```bash
docker build -t versatile/cassandra:latest cassandra-single-node/.
```

### Run you container
Run container with port mapping for external connexion
* the -v /data/cassandra:/var/lib/cassandra option persist cassandra data on your local machine

```bash
docker run -v /data/cassandra:/var/lib/cassandra -d -p 9042:9042 -p 9160:9160 --name cassandra versatile/cassandra
```

Now you can enjoy your locally persisted single node cassandra.

### Additional informations

- 7000 : intra-node communication
- 7001 : TLS inrra-node communication
- 7199 : JMX
- 9042 : CQL
- 9160 : thrift service


