# Docker file for Hadoop 3 by Ravishankar Nair

Most of the work is coming from : http://bigdatums.net/2017/11/04/creating-hadoop-docker-image/

Just added a few adaptations for Hadoop 3.

For some details about Hadoop 3 (such as new ports), see: https://fr.slideshare.net/HadoopSummit/hadoop-3-in-a-nutshell

> Please, read the content of Dockerfile, because it may be possible that you have to update it.
> See the comments about the tgz of hadoop3.

> After starting the container, you can access the web UI:
> * HDFS: http://localhost:9870
> * RM: http://localhost:8088


> Warning: hue is not fully functional... Its integration is a work in progess (file browsing is ok) !


## How-to

* Build the image
```sh
sudo docker build -t hadoop3 .
```


* Run the container
```sh
sudo docker run --hostname=hadoop3 -p 8088:8088 -p 9870:9870 -p 9864:9864 -p 19888:19888 \
  -p 8042:8042 -p 8888:8888 --name hadoop3 -d hadoop3
```

* Access the container
```sh
sudo docker exec -it hadoop3 bash
```

* Test a job
```sh
yarn jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-3.1.1.jar pi 10 100
```

* Clean
```sh
sudo docker stop hadoop3 
sudo docker rm hadoop3 
```

## Next steps

| Product/Framework/Env. | Version | (R)equired/((O)ptional |
| --- | --- | --- |

| Hive | Latest | R |
| Kafka |  Latest| O |
| Spark | Latest | O |




