minikube version
minikube start --driver=docker
minikube status
minikube kubectl -- get pods -A
minikube dashboard
kubectl version --client

minikube automation steps:
minikube start
kubectl create deployment mynginx --image=nginx
kubectl get deployments
kubectl get pods
kubectl describe pods
kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80
kubectl scale deployment mynginx --replicas=4
kubectl get service mynginx
kubectl port-forward svc/mynginx 8081:80

stop nginx deployment:
kubectl delete deployment mynginx
kubectl delete service mynginx
minikube stop


Nagios Automation steps:
docker pull jasonrivers/nagios:latest
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest
http://localhost:8888
Username: nagiosadmin
Password: nagios
docker stop nagiosdemo
docker rm nagiosdemo





this is the code for frontend pipeline {
    agent any  
    tools {
        maven 'MAVEN-HOME'
    }
    stages {         
        stage('git repo & clean') {
            steps {
                bat "git clone https://github.com/yourname/yourrepo.git"
                bat "mvn clean -f mavenjava"
            }
        }
        stage('install') {
            steps {
                bat "mvn install -f mavenjava" 
            }
        }
        stage('test') {
            steps {
                bat "mvn test -f mavenjava"
            }
        }
        stage('package') {
            steps {
                bat "mvn package -f mavenjava"
            }
        }
    }
}
