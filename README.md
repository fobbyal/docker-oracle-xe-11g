# docker-oralce-xe-11g

The Dockerfile is based off of [wnameless/oracle-xe-11g](https://github.com/wnameless/docker-oracle-xe-11g). 

## Why
The reason for creating this customized repo is to add the feature of initializing DB at build time. The original project has a way of initializing the db but the scripts runs on every container start. This maybe desired for some users, however not so much in my use case. The purpose of using docker-oracle-xe-11g for my projects is always to stand up an oracle
database with a predictable state for the purpose of running end-to-end tests. Therefore, the init feature has been added to the project. 


## Creating Docker Files
Example Docker file
```
from fobbyal/oracle-xe-11g
ADD . /init/
RUN /init.sh
```
The above docker file will then run all scripts ***`.sql` as well as `.sh` in the files that are copied to the /init directory.
Please note that this is only done once at Build-time of the Docker image. Any container that are started using the built image will start with data that was already manipulated ate buildtime.


## Usage
Please refer to [wnameless/oracle-xe-11g](https://github.com/wnameless/docker-oracle-xe-
    11g) for detailed usage
