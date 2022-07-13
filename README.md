Age/Gender prediction model has been deployed as follows:

Flask application.
•	Backend - Flask (Python) 
•	Frontend - ReactJS (HTML/JavaScript) 
Backend 
•	Python does the predicting work 
•	We have `predictModel.py` which will do the modelling and save respective model into pickle file 
•	`genderModel.pkl` will be used to predict gender 
•	`ageModel.pkl` will be used to predict age 
•	`df_classes.pkl` - this pickle holds the information of label encoded respective classes. Helpful to retransform and find the actual value. 
•	`test_data.pkl` - this pickle holds the sample 50 test data. 
•	`app.py` - This is the main flask app that initiates and creates endpoints 
•	Dockerfile - This file has a list of steps which are performed when a docker image is created

Frontend 
•	Frontend application is developed using reactJs and material ui framework 
•	App.js holds the main application entry point 
•	TableComponent.js - render the predict data - using /predict endpoint 
•	package. json - has all the dependencies to build the FE package
How to get this running (local env) 
•	This whole app can be dockerized. 
•	Before doing that, we need build our frontend (we can enhance it to separate frontend docker) 
•	cd /client/age_gender_prediction - and run npm install to download frontend dependencies 
•	run npm run build - frontend will be compiled and packed into build folder 
•	Once this is done, we can run docker from the root 
•	Dockerfile has to configuration to create docker images 
•	run sudo docker build -t age_gender_prediction. to create docker image 
•	run docker images -a to verify docker image 
•	run sudo docker run -p 5000:5000 age_gender_prediction to run the docker 
•	if you are running on local - verify it on browser via localhost:5000

DEPLOYING IN AWS EC2 INSTANCE
Create Instance 
Choose the Amazon Machine Image (AMI)
Choose an Instance Type (m4.xlarge)
Clone Flask app from git repository: 
● Install git - sudo yum update -y && sudo yum install git -y 
● run - git clone git@github.com:<Your Git>
NPM install on ec2 instance:
•	npm install to update frontend dependencies - if any
•	Run npm run build command to compile/build the frontend
•	Run sudo yum install docker - to install docker - since I have already installed below logs in the screenshot

•	Run sudo service docker start - to initialize docker in EC2
•	Go to our project root folder - run docker build -t age_gender_prediction.
•	Run docker images -a to see the list of images create
•	Run docker run -p 5000:5000 age_gender_prediction to start the docker container

Finally open the application with the provided DNS address.
