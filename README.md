# docker-run
## update packages or execute arbitrary commands inside running docker containers

Quick use: `docker run --rm -v /var/run/docker.sock:/tmp/docker.sock itech/docker-run exec`

By default *exec* will execute `date` command in all running containers

`docker run --rm -v /var/run/docker.sock:/tmp/docker.sock itech/docker-run exec "uname -a"`

To update packages (only debian/ubuntu containers at the moment)

`docker run --rm -v /var/run/docker.sock:/tmp/docker.sock itech/docker-run update`

