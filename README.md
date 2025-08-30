A simple python flask app prints "Hello from DevOps Pipeline!"
Developed this sample project by integrating DevOps toolset.
My flask app is exposed at the port 5320
Jenkinsfile is doing the below steps:
    . clones the source code from my github repository
    . builds the docker image
    . login to the dockerhub account
    . pushes the image to my dockerhub account
Then come to the command line and run the deploy-flask.yaml file.
This file will create both the deployment and service for my flask app
This exposes my app at the nodeport 30010
Open your browser and type http://localhost:30010
