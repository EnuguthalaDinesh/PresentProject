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
