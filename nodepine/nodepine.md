# cjherold/nodepine
## Alpine linux with node and npm installed

#### Example run command
```bash
docker pull cjherold/nodepine:latest
docker run --name myname -it -p 3000:8888 cjherold/nodepine
```
###### (-p HOST:CONTAINER)

#### Access shell of running container from terminal
```bash
# bash 
docker exec -it containerid /bin/bash
# sh
docker exec -it containerid /bin/sh
```

<ul>
    <li>nano editor is installed</li>
    <li>bash installed</li>
    <li>node v12.15.0</li>
    <li>npm 6.13.4</li>
</ul>

