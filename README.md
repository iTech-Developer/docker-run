# docker-run
#### update packages or execute arbitrary commands inside running docker containers

When running multiple containers, updating the packeges, including security updates, in all of them can be a time consuming job.

`docker-run` can be used to issue any arbitrary command on all running containers or a specified subset.

Quick use: `docker run --rm -v /var/run/docker.sock:/tmp/docker.sock itech/docker-run exec`

By default *exec* will execute `date` command in all running containers

The easiest way to use it is to create an alias, so you just execute `docker-run` directly as a regural command

`alias docker-run='docker run --rm -v /var/run/docker.sock:/tmp/docker.sock itech/docker-run'`

If connecting to docker daemon over http you can specify the docker daemon host:port

`alias docker-run='docker run --rm itech/docker-run --host http://127.0.0.1:4243'`

Examples (assumig you have the alias):

- `docker-run exec "uname -a"` 
  *display the kernel in each container*

- `docker-run update`
 *will update packages (only debian/ubuntu containers at the moment)*
- `docker-run update -p python`
  *will only update python package*

- `docker-run -c db1,db2 update postgresql`
  *only update the postgresql package on container db1 and db2* containers with these names must exist

- `docker-run -c my_centos exec "yum update -y"`
  *will update a container names 'my_centos'*

