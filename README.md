# docker-run
#### *update packages or execute arbitrary commands inside running docker containers*

When running multiple containers, updating the packeges, including security updates, in all of them can be a painful task.

`docker-run` can be used to issue any arbitrary command on all running containers or a specified subset.

Quick use: `docker run --rm -v /var/run/docker.sock:/tmp/docker.sock itech/docker-run exec`

By default *exec* will execute `date` command in all running containers

-
### Usage

The easiest way to use it is to create an alias, so you just execute `docker-run` directly as a regural command

`alias docker-run='docker run --rm -v /var/run/docker.sock:/tmp/docker.sock itech/docker-run'`

If connecting to docker daemon over http you can specify the docker daemon host:port

`alias docker-run='docker run --rm itech/docker-run --host http://127.0.0.1:4243'`

--

### Examples
*assumig you have the alias*

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

- `docker-run exec "date +'%Y-%m-%d' && uname -r"`
  *example of running multiple commands with different parameter for each*

--
## LICENSE
Copyright 2014 iTech-Developer

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
