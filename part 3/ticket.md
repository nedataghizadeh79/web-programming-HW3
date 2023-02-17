## changes:

don't forget to change this line at model.js:

```JS
const sequelize = new Sequelize('postgres://postgres:secretpassword@host.docker.internal:8080/postgres')
```

## Dockerfile

this file is placed at the root directory

<div>

```Dockerfile
FROM node:19

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm ci --only=production

# Bundle app source
COPY . .

EXPOSE 3000
CMD [ "node", "app.js" ]
```

</div>

## command

```bash
docker pull node
sudo docker build . -t shahab/node-web-app
sudo docker run -p 3000:3000 --add-host=host.docker.internal:host-gateway -d shahab/node-web-app
```

## output

```
Sending build context to Docker daemon  78.63MB
Step 1/7 : FROM node:19
 ---> 272b8142e84e
Step 2/7 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 5880c7945c49
Step 3/7 : COPY package*.json ./
 ---> Using cache
 ---> a0562ef76202
Step 4/7 : RUN npm install
 ---> Using cache
 ---> 524fa3748a8f
Step 5/7 : COPY . .
 ---> c209633b0452
Step 6/7 : EXPOSE 3000
 ---> Running in 2d15501a6f24
Removing intermediate container 2d15501a6f24
 ---> 8c3bc1cf9ed6
Step 7/7 : CMD [ "node", "app.js" ]
 ---> Running in 42ef4bfeec96
Removing intermediate container 42ef4bfeec96
 ---> 620cb4779817
Successfully built 620cb4779817
Successfully tagged shahab/node-web-app:latest
a6ad9d09c3873240270266e2c1597db55317efc64800e08e26b9a1bc91e8609f
```

## testing

now we can send requestst to the service:

![ticket1.png](./ticket1.png "ticket1.png")
![ticket2.png](./ticket2.png "ticket2.png")