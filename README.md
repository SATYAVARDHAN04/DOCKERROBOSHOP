### STEP 1: INSTALL DOCKER

### STEP 2: CONFIGURE MONGODB IMAGE AND CONTAINER

**LOAD DEMO DATA FROM CATALOGUE**

```bash
docker build -t mongodb:v1 .
```

```bash
docker run -d --name mongodbcontainer mongodb:v1
```

### STEP 2: CONFIGURE CATALOGUE IMAGE AND CONTAINER

```bash
docker build -t catalogue:v1 .
```

```bash
docker run -d --name cataloguecontainer catalogue:v1
```

### STEP 3: CREATE A NEW NETWORK

```bash
docker network create roboshop
```

### STEP 4: DISCONNECT FROM OLD BRIDGE NETWORK

```bash
docker network disconnect bridge cataloguecontainer
```

```bash
docker network disconnect bridge mongodbcontainer
```

### STEP 5: CONNECT TO NEW ROBOSHOP NETWORK

```bash
docker network connect roboshop cataloguecontainer
```

```bash
docker network connect roboshop mongodbcontainer
```

### STEP 6: SET UP REDIS CONTAINER

IN THE SAME CONTAINER OF CATALOGUE WE CAN PULL REDIS CONTAINER IMAGE

```bash
docker run -d --name rediscontainer --network roboshop redis:7
```

### STEP 7: SET UP USER CONTAINER

```bash
docker build -t user:v1 .
```

```bash
docker run -d --name usercontainer --network roboshop user:v1
```

### STEP 8: SET UP CART CONTAINER

```bash
docker build -t cart:v1 .
```

```bash
docker run -d --name cartcontainer --network roboshop cart:v1
```

### STEP 9: SET UP MYSQL CONTAINER

**LOAD DEMO DATA FROM SHIPPING**

```bash
docker build -t mysql:v1 .
```

```bash
docker run -d --name mysqlcontainer --network roboshop mysql:v1
```

### STEP 10: SET UP SHIPPING CONTAINER

```bash
docker build -t shipping:v1 .
```

```bash
docker run -d --name shippingcontainer --network roboshop shipping:v1
```

### SOME IMPORTANT COMMANDS TO KNOW

```bash
docker logs <container_name>
```

```bash
docker exec -it <container_name>/<container_id>
```

```bash
docker network ls
```

```bash
docker inspect <container_name>
```

**LOOKS FOR CONTAINER INFO LIKE IP ADDRESS, PORT OPENED, DNS**

```bash
for i in mongodb catalogue user cart mysql shipping payment;do cd $i;docker build -t satyology/$i .;docker push satyology/$i;done
```
