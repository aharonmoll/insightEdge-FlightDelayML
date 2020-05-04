# PartnerWorkShop 
## Lab-3: Deploy a machine learning pipeline
* load data , enrich , train the model and predict Participants will use various industry leading building blocks such as spark , kafka and in-memory processing

### In this lab you will setup This sample application uses flight delay data to make binary predictions (yes/no) about which flights are likely to get delayed.
### The lab will be based on Lab-1 (gsctl)

Please perform the following steps:

1. Create gsctl cluster (as you did in lab 1).
2. Go to scripts directory and Copy zeppelin_setup.sh to the zeppelin node.
3. Run zeppelin_setup.sh in zeppelin node home directory:
   `/home/ec2-user/zeppelin_setup.sh`
   This scripts will download flight delay data to zeppelin node (machine).
4. Change artifact-repo to https://amoll.s3-eu-west-1.amazonaws.com/Services
5. Deploy flight_delay space: 
   `deploy --type=stateful --memory=2048 flights_space flight-delay-0.1.jar`
6. Import two zeppelin notebooks from zeppelin_notebooks directory:
   ![snapshot](Pictures/Picture1.png)
7. Change space name to “flights_space” in insightedge_jdbc interpreter<br>
   ![snapshot](Pictures/Picture2.png)
8. Run all zeppelin paragraphs (one by one) until you reach the Kafka paragraph.<br>
   Before continuing to the kafka section your zeppelin last paragraph should yield the following accuracy = 0.79<br>
   ![snapshot](Pictures/Picture3.png)
   Flights_space should have the following number of records:<br>
   ![snapshot](Pictures/Picture4.png)
9. Deploy flights_feeder:
   `deploy --type=stateless --property=feeder.flights.path=/home/ec2-user/data.csv --property=kafka.bootstrapServer=kafka-0.service.consul:9092 flights_feeder kafka-pers-feeder.jar`
10. Continue running the kafka streaming paragraph.
11. Verify you have new FlightDelaysWithWeather where year=2019 and prediction = 'for_calc'
12. Read the Flights data from the memory grid and run our model prediction on it.
13. Run remaining zeppelin paragraph.<br>
14. Last paragraph view should look something like:<br>
    ![snapshot](Pictures/Picture5.png)
15. You are done with the lab!!!
    Don't forget to **teardown** the cluster as described in Lab-1.
    






