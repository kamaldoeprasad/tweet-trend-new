pipeline {
    agent {
        node {
            label "maven-slave"
        }
    }

environment {
    PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
}

    stages {
        stage('Clone-code') {
            steps {
                sh 'mvn clean deploy' 
            }
        }
        stage('SonarQube analysis') {
        environment {
         scannerHome = tool 'sonar-scanner'
         }   
        steps{
          withSonarQubeEnv('sonarqube-server')
         sh "${scannerHome}/bin/sonar-scanner"
        }
      
    }
    }
}
