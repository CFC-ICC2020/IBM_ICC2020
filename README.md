**** IBM Services to be deployed ****
	Node-Red
	Watson IoT
	Watson Studio
	Cloudant DB - With 4 databases
		1- db_water_store
		2- db_houseicc2020_usage
		3- houseicc_daily_usage
		4- General DB - for storing node red flows
	Watson chatbot
	Twilio service

**** Nodes to be installed in Node Red ****
	node-red-dashboard
	node-red-contrib-ibm-watson-iot
	node-red-contrib-python3-function
	node-red-contrib-sms-twilio
	node-red-contrib-watson-machine-learning
	node-red-node-cf-cloudant
	node-red-node-watson
	
**** External accounts ****
	A trial account in Twilio to send SMS

**** Auto AI experiments ****
	Trained fours ML models in Watson Auto AI.

>>Provided node red json fow. Import the flow in node red.

**** Changes to be made in flow to run in any Node red ****

>> Update the IoT sensor details as per your deployed service.
>> Update the Cloudant DB instance.
>> Update the Twilio account.
>> Update ML model instance ID and API key

**** Short Description ****

>> Water usage in a house varies based on time. So, simulation of usage data (to be synchronous with original data) should be done based on time. Input to Watson IoT simulated sensor is given from Node red based on current timestamp.

>> The sensor data uploaded to Watson IoT is transferred to Node red and the data is uploaded in Cloudant DB - "db_houseicc2020_usage" with current date and timestamp.

>> At every day 00:00 am the cosolidated water usage of previous day is calculated and is updated in another cloudant DB - "houseicc_daily_usage"

>> With the obtained data for consolidated water usage, a ML model is created in Watson Auto AI.

>> A parameter called "Water Recharge" which refers the amount of water that is getting recharged back to ground so as to enhance current solution to ground water is also taken into account.
	
	**** Recharge Calculation ****
	>> Recharge will depends on following factors:
		>. Evaporation - which depends on temperature
		>. Humidity
		>. Rainfall and 
		>. Rocks and soil texture in an area
		>. Type of usage - (Household, Industries or Agriculture etc..,)
	So, Considering the above factors we concluded to take recharge as percentage of usage that depends on various seasons (Summer, Winter,Autumn,Spring) - (Which determines temerature, humidity and rainfall)
	
>> The proposed solution finds complexity in calculating actual ground water. So, repacing ground water to central water storage. (Ground water calculation will be taken care in future)

>> ML models are trained and deployed and is connected to node red.

>> Prediction of Day Zero is done and a dashboard is generated for end users.

>> Leakage sensors are simulated from Watson IoT and the data is transmitted to node red.

>> Periodic SMS is also configured for Leakage. 

Note: Views are created to filter required data from Cloudant DB. The code for views is also provided.

AUTHOR:
raghavsankarv@gmail.com
