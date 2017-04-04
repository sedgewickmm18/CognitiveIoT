### Fly in the ointment

or

### Properly sizing a Flink deployment

There are a couple of references how to size Hadoop, for example [here](https://0x0fff.com/hadoop-cluster-sizing/); however, I'm not sure how they apply to our use case.

Based on Ron Crocker's NewRelic minute aggregator [experiments](https://www.slideshare.net/FlinkForward/ron-crocker-evaluating-streaming-framework-performance-for-a-largescale-aggregation-pipeline) we came up with the following
![Overview](https://github.com/sedgewickmm18/diagrams/blob/master/FlinkSoftlayer-RHT-20032017.png)
<br> to address up to 500k events per second.<br>

It would be really helpful if there was more public information on Flink deployments.
