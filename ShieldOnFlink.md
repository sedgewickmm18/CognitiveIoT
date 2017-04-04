#### What is a shield

Shield are complex event expressions like

<code> 
If (WaterleakSensor has fired) &&<br>
&nbsp; if (another waterleakSensor has fired) &&<br>
&nbsp; &nbsp; while "I'm away"<br>
&nbsp; &nbsp; &nbsp; then send push notification
   </code><br>

or an even more complex example
![Elderly care](https://github.com/sedgewickmm18/diagrams/blob/master/IoT4I%20-%20ElderlyCare.png)


#### Shield on Bluemix

[Real Life: Flink on Bluemix](http://134.168.58.194:8081/#/overview)

<small>*no kubernetes due to 4 GB barrier on beta<br>

#### Shield engine on Flink

[Elderly Care Shield - Job.scala](https://github.ibm.com/IoT-Insurance/flink-pocs/blob/master/medium-complex-shields/elderly-care-shield/src/main/scala/ibm/Job.scala) <br>
[Elderly Care Shield - EventProcessFunction.scala](https://github.ibm.com/IoT-Insurance/flink-pocs/blob/master/medium-complex-shields/elderly-care-shield/src/main/scala/ibm/EventProcessFunction.scala)

#### What about the throughput ?

[Our results so far](LocalMosquitto.md)

