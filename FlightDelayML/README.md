# FlightDelayML Lab 
## Lab-1: Deploy a machine learning pipeline
* load data , enrich , train the model and predict Participants will use various industry leading building blocks such as spark , kafka and in-memory processing

### In this lab you will:
#### 1. Create an InsightEdge cluster
#### 2. Deploy an application which consumes flight delay data to make binary predictions (yes/no) about which flights are likely to get delayed.

Please perform the following steps:

1. Run InsightEdge:<br>
   `./gs.sh host run-agent --auto`
2. Create 2g container (use the cli):<br>
   `container create --memory 2g localhost`<br>
3. Deploy flight_delay space<br>
   `pu deploy flights_space ~/FlightDelayML/flightDelaySpace/target/flight-delay-0.1.jar`<br>
4. Open zeppelin and import the two notebooks from zeppelin_notebooks directory<br>
   ![snapshot](Pictures/Picture1.png)<br>
5. Change space name to “flights_space” in insightedge_jdbc interpreter<br>
   ![snapshot](Pictures/Picture2.png)<br>
6. Run all zeppelin paragraphs (one by one) until you reach the Kafka paragraph.<br>
   Before continuing to the kafka section your zeppelin last paragraph should yield accuracy ~ 0.80<br>
   ![snapshot](Pictures/Picture3.png)<br>
   Flights_space should have the following number of records:<br>
   ![snapshot](Pictures/Picture4.png)<br>
7. Download and run kafka:
   * https://archive.apache.org/dist/kafka/0.11.0.0/kafka_2.12-0.11.0.0.tgz
   * tar zxvf kafka_2.12-0.11.0.0.tgz
   * ~/kafka_2.12-0.11.0.0/bin/kafka-server-start.sh ../config/server.properties 
   * In a new session run:
   ~/kafka_2.12-0.11.0.0/bin/kafka-console-consumer.sh --topic flights --zookeeper localhost:2181 
   
8. Deploy flights_feeder:<br>
   `pu deploy flights_feeder ~/FlightDelayML/kafkaFeederPU/target/kafka-pers-feeder.jar`<br><br>
9. In the kafka-console-consumer.sh session you should see coming messages:<br>
   ![snapshot](Pictures/Picture5.png)<br>
8. Continue running the kafka streaming paragraph and the remaining zeppelin paragraphs.<br>
9. Last paragraph view should look something like:<br>
    ![snapshot](Pictures/Picture6.png)<br>
10. You are done with the lab!!!<br>
    
    






