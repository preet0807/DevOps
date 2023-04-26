pipeline {
    agent any

    
    stages {
        stage('Git Checkout') {
            steps {
                // Checkout code from Github repository
               git branch: 'main', url: 'https://github.com/preet0807/DevOps.git'
            }
        }
        stage ('UNIT testing'){
            steps{
                sh 'mvn verify -DskipUnitTests'
            }
        
        }
        stage('Maven Build'){
            steps{
                sh 'mvn clean install '
            }
        }
    }



        
