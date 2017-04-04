
### Locally deployed mosquitto + JMeter

Driving events into Flink with a locally deployed mosquitto running JMeter on the same docker container

<br>

#### This time [more is really better](http://www.energy2engage.com/hs-fs/hub/129961/file-296483410-jpeg/images/more_is_better.jpeg?t=1490990984108&width=400&height=300&name=more_is_better.jpeg)

[Real Life: Flink on Bluemix](http://134.168.58.194:8081/#/overview)

#### Two metrics examples  
(Flink 1.2.0)

![Metric #1](metrics-source.jpeg)
![Metric #2](metrics-source-2.jpeg)

NFS and mosquitto are responsible for the staircase like appearance.

<br><br>
While the results in general look satisfying, a container deployment is not suitable for large customers or a multitenant deployment, i.e. multiple customers sharing a single Flink installation - maybe with separate taskmanagers.

[Sizing a Flink deployment](FlyInTheOintment.md)



