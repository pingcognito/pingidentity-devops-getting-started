
# Ping Identity DevOps Docker Image - `pingfederate`

This docker image includes the Ping Identity PingFederate product binaries
and associated hook scripts to create and run both PingFederate Admin and
Engine nodes.

## Related Docker Images
- pingidentity/pingbase - Parent Image
- pingidentity/pingcommon - Common Ping files (i.e. hook scripts)
- pingidentity/pingdownloader - Used to download product bits

## Ports Exposed
The following ports are exposed from the container.  If a variable is
used, then it may come from a parent container
- 9031
- 9999

## Environment Variables
The following environment `ENV` variables can be used with 
this image. 

| ENV Variable  | Default     | Description
| ------------: | ----------- | -------
| PING_PRODUCT  | PingFederate  | 
| LICENSE_DIR  | ${SERVER_ROOT_DIR}/server/default/conf  | 
| LICENSE_FILE_NAME  | pingfederate.lic  | 
| LICENSE_SHORT_NAME  | PF  | 
| LICENSE_VERSION  | 9.2  | 
| OPERATIONAL_MODE  | STANDALONE  | 
| CLUSTER_BIND_ADDRESS  | NON_LOOPBACK  | 
| STARTUP_COMMAND  | ${SERVER_ROOT_DIR}/bin/run.sh  | 
| TAIL_LOG_FILES  | ${SERVER_ROOT_DIR}/log/server.log  | 
## Running a PingFederate container
To run a PingFederate container:

```shell
  docker run \
           --name pingfederate \
           --publish 9999:9999 \
           --detach \
           --env SERVER_PROFILE_URL=https://github.com/pingidentity/pingidentity-server-profiles.git \
           --env SERVER_PROFILE_PATH=getting-started/pingfederate \
           pingidentity/pingfederate
```

Follow Docker logs with:

```
docker logs -f pingfederate
```

If using the command above with the embedded [server profile](../server-profiles/README.md), log in with:
* https://localhost:9999/pingfederate/app
  * Username: Administrator
  * Password: 2FederateM0re

---
This document auto-generated from _[pingidentity/pingfederate Dockerfile](https://github.com/pingidentity/pingidentity-docker-builds/blob/master/pingfederate/Dockerfile)_

Copyright (c)  2019 Ping Identity Corporation. All rights reserved.