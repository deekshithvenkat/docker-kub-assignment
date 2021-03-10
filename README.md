# Task-1
## prerequisites
- install docker and dcoker-compose
- Update requirements.txt with psutil, flask, flask_cors
- install dependencies using `pip3 -r requirements.txt`
- npm install 
- cp docker/Dockerfile-python <Absolute path to DevOps-Assignment>/Dockerfile
- cp docker/Dockerfile-react <Absolute path to DevOps-Assignment>/sys-stats/Dockerfile
- cp docker/docker-compose.yml default.conf <Absolute path to DevOps-Assignment>/.

## Running Application
- Run command `docker-compose up --build`
- Open browser and run http://localhost => you can see application is running 

# Task-2
- Create Ec2 instance and add security group to expose only ports 80 and 22.
- Port 22 is used to ssh into server
- Assign static IP address to instance
- push docker images to dockerhub ex: smartcow/api:latest, smartcow/react:latest
- Run sudo docker-compose up --build -d => you can access application from staticIp

# Task-3
- Before creating react application dockerimage update python app uri as http://api.smartcow.default.svc.cluster.local:5000/stats
- Assuming docker images are smartcow/api:latest, smartcow/react:latest, nginx:latest
- create 3 pod, one pod for each service
- create a headless service which provides DNS name to pod
- create a service to bind on ports provided by kubernetes
- Running single instance of Nginx for whole cluster which will be placed in kubernetes master server
  - nginx will be listening on 80 and all other ports of kubernetes master will be closed
  - use nginx configuration to redirect request to application ports provided by kubernetes
  
## Run application in kubernetes
- All pod and service files are available in kubernetes directory
- launch app => kubectl create -f ./kubernetes/

