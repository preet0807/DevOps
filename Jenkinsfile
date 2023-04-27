pipeline {
    agent any
     tools {
    maven 'maven 3.9.1' 
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
                sh '/C:/Program Files/apache-maven-3.9.1-bin/apache-maven-3.9.1/mvn clean install'
            }
        }
      
          }
    }



        
