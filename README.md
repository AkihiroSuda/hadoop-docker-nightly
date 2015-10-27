# Nightly Docker Image for Hadoop (built upon request)

[Docker Hub](https://hub.docker.com/r/akihirosuda/hadoop-docker-nightly/tags/)

## Usage
The image is very vanilla. i.e., it does not include any init script. (so as to improve flexibility)

For YARN, you might need to start ssh manually.
    
    host$ docker run -i -t --rm akihirosuda/hadoop-docker-nightly:20151027
	docker$ service ssh start
	 * Starting OpenBSD Secure Shell server sshd                    [ OK ] 
	docker$ start-yarn.sh
    Starting resourcemanager
    Starting nodemanagers
    docker$ curl -s http://localhost:8042/ws/v1/node/info | json_pp
    {
       "nodeInfo" : {
          "hadoopVersionBuiltOn" : "2015-10-27T07:02Z",
          "nodeHostName" : "575c3286a28b",
          "healthReport" : "",
          "totalPmemAllocatedContainersMB" : 8192,
          "hadoopBuildVersion" : "3.0.0-SNAPSHOT from Unknown by root source checksum eeb72a47662962ad7d8154badde51a5",
          "nodeManagerBuildVersion" : "3.0.0-SNAPSHOT from Unknown by root source checksum 75c87ccc55e11c3edba88ebff9277c5",
          "nodeManagerVersion" : "3.0.0-SNAPSHOT",
          "lastNodeUpdateTime" : 1445931265519,
          "nodeHealthy" : true,
          "vmemCheckEnabled" : true,
          "hadoopVersion" : "3.0.0-SNAPSHOT",
          "nmStartupTime" : 1445931264643,
          "nodeManagerVersionBuiltOn" : "2015-10-27T07:11Z",
          "totalVCoresAllocatedContainers" : 8,
          "id" : "575c3286a28b:39743",
          "totalVmemAllocatedContainersMB" : 17203,
          "pmemCheckEnabled" : true
       }
    }
    

## Build Manually
    
    host$ git submodule --init update
    host$ docker build -t hadoop-docker-nightly .
    
