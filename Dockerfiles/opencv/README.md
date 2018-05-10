## Dockerfile for compiling OpenCV and compress it to `tar.gz`:

Steps:

```sh
$ docker build -t buildpack-opencv3 .
$ docker run -it buildpack-opencv3:latest  /bin/bash
$ docker ps
# CONTAINER ID        IMAGE                          COMMAND                  CREATED
# 37d87ca08707        buildpack-opencv3:latest       "/bin/bash"              10 seconds ago

$ docker cp 37d87ca08707:/root/heroku16-buildpack-opencv3.4.1.tar.gz ./
```
