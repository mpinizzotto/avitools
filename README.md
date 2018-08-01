# Overview
## avinetworks/avitools docker image
Description: Container is designated to host all the required migration and verification tools needed in the field for successful customer migration. Please refer for the Dockerfile for the list of included tools.

# Usage
## Docker image can be consumed using run.sh script under git:avinetworks/avitools/scripts/run.sh
```bash
$ curl -O https://raw.githubusercontent.com/avinetworks/avitools/master/scripts/run.sh
$ chmod a+x run.sh
$ ./run.sh --help
./run.sh: illegal option -- -
-v string    specify AVI_VERSION, default value: 18.1.3
-c string    specify CMD to execute, in this mode container will be created and destroyed on command run, default value: avitools-list
-d string    specify working directory, where configuration files will exist, default value: /Users/avi
-u           update docker image, i.e. try to pull docker image again
-b           run in background, other words create avitools container and retain it, container can be accessible after script execution, for example as "docker exec -it avitools bash", default value: avitools-list
```
## Using -v flag you can specify the container version, otherwise default value will be assumed.

## To show the commands supported by avitools
```
$ ./run.sh -c avitools-list or ./run.sh or ./run.sh -v 18.1.2 -c avitools-list
```
## To show the commands supported by avitools 18.1.2 version of container
```
$ ./run.sh -v 18.1.2 -c avitools-list
```
## How to run commands using run.sh
```
ex. sh run.sh -v <AVI_VERSION> -d <DIR> -c <COMMAND>
$ ./run.sh -c "f5_converter.py -h"
$ ./run.sh -c "f5_converter.py -f <filename>"
$ ./run.sh -v 18.1.2 -d /home/aviuser -c "f5_converter.py -h"
$ ./run.sh -v 18.1.2 -d /home/aviuser -c "f5_converter.py -f <filename>"
```

## To run ansible playbook
```
$ ./run.sh "ansible-playbook <playbook-name> -v"
```
## To run container in background
```
$ ./run.sh -v 18.1.2 -c bash -d /Users/smarunich/workspace -b
$ docker exec -it avitools bash
```

## Optional
### Build instructions
```
cd build
docker build -t avinetworks/avitools:18.1.2 .
```
### How you can use migrationtools docker image
First you need to build a docker image
Run the run.sh which is in scripts directory to run avitools on that image