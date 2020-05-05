# PartnerWorkShop 
## Lab-3: Deploy a machine learning pipeline
* load data , enrich , train the model and predict Participants will use various industry leading building blocks such as spark , kafka and in-memory processing

### In this lab you will setup This sample application uses flight delay data to make binary predictions (yes/no) about which flights are likely to get delayed.
### The lab will be based on Lab-1 (gsctl)

Please perform the following steps:

<b>1.</b> Create gsctl cluster (as you did in lab 1).<br>
<b>2.</b> Change artifact-repo to https://amoll.s3-eu-west-1.amazonaws.com/Services<br>
<b>3.</b> Deploy flight_delay space: <br>
   `deploy --type=stateful --memory=2048 flights_space flight-delay-0.1.jar`<br>
<b>4.</b> Open zeppelin (<"manager host">:9090)<br>
<b>5.</b> Import two zeppelin notebooks from zeppelin_notebooks directory:<br>
   ![snapshot](Pictures/Picture1.png)<br>
<b>6.</b> Change space name to “flights_space” in insightedge_jdbc interpreter<br>
   ![snapshot](Pictures/Picture2.png)<br>
<b>7.</b> Run all zeppelin paragraphs (one by one) until you reach the Kafka paragraph.<br>
   Before continuing to the kafka section your zeppelin last paragraph should yield the following accuracy = 0.79<br>
   ![snapshot](Pictures/Picture3.png)<br>
   Flights_space should have the following number of records:<br>
   ![snapshot](Pictures/Picture4.png)<br>
<b>8.</b> Deploy flights_feeder:<br>
   `deploy --type=stateless --property=feeder.flights.path=/home/ec2-user/data.csv --property=kafka.bootstrapServer=kafka-0.service.consul:9092 flights_feeder kafka-pers-feeder.jar`<br><br>
<b>9.</b> Continue running the kafka streaming paragraph and the remaining zeppelin paragraphs.<br>
<b>10.</b> Last paragraph view should look something like:<br>
    ![snapshot](Pictures/Picture5.png)<br>
<b>11.</b> You are done with the lab!!!
    Don't forget to **teardown** the cluster as described in Lab-1.
    






