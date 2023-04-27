pipeline {
    agent any
    tool {
        tool name: 'maven 3.9.1', type: 'maven'
    }

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
        
       
        stage('Build'){
            steps{
                bat '/C:/Program Files/apache-maven-3.9.1-bin/apache-maven-3.9.1/bin/mvn clean install'
            }
        }
         
          }
}



        
