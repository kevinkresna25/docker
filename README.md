# DOCKER

## Commands

### Cek Version
```
docker version
```

### Melihat Docker Image
```
docker image ls
```


### Download Docker Image
```
docker image pull namaimage:tag
```
**Example:**
```
docker image pull redis:latest
```


### Menghapus Docker Image
```
docker image rm namaimage:tag
```
**EX**
```
docker image rm redis:latest
```


### Melihat Container
```
docker container ls
```
or (all)
```
docker container ls -a
```


### Membuat Container
```
docker container create --name namacontainer namaimage:tag
```
**EX**
```
docker container create --name contohredis redis:latest
```


### Melakukan Port Forwarding
```
docker container create --name namacontainer --publish porthost:portcontainer image:tag
```
or
```
docker container create --name namacontainer -p porthost:portcontainer image:tag
```

> [!NOTE]
> 1. Port Forwading harus dilakukan saat membuat CONTAINER, harus mempunyai IMAGE terlebih dulu.
> 2. Jika ingin melakukan port forwading lebih dari satu, bisa tambahkan dua kali parameter --publish bisa disingkat -p.

**EX**
```
docker container create --name contohnginx -p 8080:80 image:tag
```


### Menambah Environment Variable
```
docker container create --name namacontainer --env KEY="value" --env KEY2="value" image:tag
```
> [!NOTE]
> 1. Lihat bagian deskripsi, apakah ada variable environmentnya atau tidak.

**EX**
```
docker container create --name contohmongo \
  -p 27017:27017 \
  --env MONGO_INITDB_ROOT_USERNAME=kresnauser \
  -e MONGO_INITDB_ROOT_PASSWORD=kresnapass \
  mongo:latest
```


### Menjalankan Container
```
docker container start containerId/namacontainer
```
**EX**
```
docker container start contohredis
```


### Menghentikan Container
```
docker container stop containerId/namacontainer
```
**EX**
```
docker container stop contohredis
```


### Menghapus Container
```
docker container rm containerId/namacontainer
```
**EX**
```
docker container rm contohredis
```


### Melihat Container Log
```
docker container logs containerId/namacontainer
```
**EX**
```
docker container logs contohredis
```
or
```
docker container logs -f contohredis
```


### Masuk ke Container
```
docker container exec -i -t containerId/namacontainer /bin/bash
```
or
```
docker exec -it containerId/namacontainer bash
```
> [!NOTE]
> -i : argument interaktif, menjaga input tetap aktif
> -t : argument alokasi pseudo-TTY (Terminal Akses)

**EX**
```
docker container exec -i -t contohredis /bin/bash
```
or
```
docker exec -it contohredis bash
```


### Container Stats / Melihat Penggunaan Resource Per Container
```
docker container stats
```


### Membuat Network
```
docker network create name
```
**EX**
```
docker network create myhome
```


### Cek Network
```
docker network ls
```

> [!NOTE]
> 1. Cara melihat port container, bisa melihat "Melihat Container".
> 2. Port pada container tidak dapat diakses oleh host kecuali menggunakan port forwarding.
