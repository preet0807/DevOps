pipeline {
    agent any
    
      environment {
        PATH = "/C:/Program Files/apache-maven-3.9.1-bin/apache-maven-3.9.1:$PATH"
    }



    
    stages {

        stage('Git Checkout') {
            steps {
                // Checkout code from Github repository
               git branch: 'main', url: 'https://github.com/preet0807/DevOps.git'
            }
        }
        
       stage('Build maven-job') {
       steps {
        build job: 'maven-job', propagate: true, wait: true
      }
    } 
           stage('SonarQube Analysis') {
            environment {
                SCANNER_HOME = tool 'SonarQube_Scanner'
            }
            steps {
                script {
                    def scannerHome = tool 'SonarQube_Scanner'
                    withEnv(["PATH+SCANNER=${scannerHome}\\bin"]) {
                        bat 'sonar-scanner.bat \
                             -Dsonar.projectKey=DevOps \
                             -Dsonar.sources=. \
                             -Dsonar.host.url=http://192.168.1.50:9000/ \
                             -Dsonar.login=sqp_9ba5e344b5a16fbb7627f5e989a765b151d70627 '
                    }
                }
            }
        }        
 }
}



        
