# Not Finished

## Cli build
#### Start by pulling. The cloudServer.js file in the container listens for port 3000 but the host just uses regular localhost
```bash
docker pull cjherold/cloud-website
docker run -it --name MYCONTAINERNAME -p 80:3000 cjherold/cloud-website
```

#### If you are in the shell of the container you can go to /home/cloud-site/ and run the following commands
```bash
npm install
npm start
```

#### If you are not in the shell/container you can run this to get into it (replace <CONTAINERID> with the id of the running container)
```bash
docker exec -it <CONTAINERID> /bin/sh
```
###### this should install the node modules and start the server
###### go to localhost.com and you should see the site 

#### To save the server logs, create a file in /home/cloud-site/ called logs.txt, then run the server like this
```bash
# create the file
touch logs.txt
# save logs to file
node cloudServer.js >> logs.txt
```
##### you won't see any output but when you ctrl+c to exit, the logs.txt file will have all the output









## Build Image With Dockerfile 
###### (save as "Dockerfile" without extension)
```yml
FROM cjherold/nodepine

COPY cloud /home/
WORKDIR /home/cloud/

RUN npm install

CMD [ "npm", "start" ]
```

```bash
docker build -t building-image-name .
```

###### don't forget the "." at the end, it is the current directory (one with dockerfile)
```bash
docker run -p 80:3000 name-of-image
```

## Compose
###### uses Dockerfile to build service then adds ports (all with one command)
```yml
version: '3.8'

services:
  cloudsite:
    # build . uses Dockerfile to make an image for this service
    build: .
    # image: name-of-already-built-image
    # server is using 3000 inside the container (Host:Container)
    ports:
    - "80:3000"
```

###### run this in the same directory as Dockerfile and docker-compose.yml
```bash
docker-compose up
```
    
