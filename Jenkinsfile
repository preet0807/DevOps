<<<<<<< HEAD
<<<<<<< HEAD
pipeline {
    agent any
    
    tools {
        // Set Maven installation
        maven 'Maven 3.6.3'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Github repository
                git url: 'https://github.com/preet0807/DevOps.git', branch: 'main'
            }
        }
        
        stage('Build') {
            steps {
                // Build the project using Maven
                sh 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                // Run automated tests
                sh 'mvn test'
            }
        }
        
        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }
        
        stage('Deploy') {
            steps {
                // Deploy the application to a server
                sh 'scp target/devops.war user@server:/opt/tomcat/webapps'
            }
        }
    }
    
    post {
        always {
            // Clean up workspace
            cleanWs()
        }
    }
}
=======
=======
>>>>>>> f914cc6a238f58ff709a293d6149226e7d50e0c4
pipeline {
    agent any
    
    tools {
        // Set Maven installation
        maven 'Maven 3.6.3'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Github repository
                git url: 'https://github.com/preet0807/DevOps.git', branch: 'main'
            }
        }
        
        stage('Build') {
            steps {
                // Build the project using Maven
                sh 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                // Run automated tests
                sh 'mvn test'
            }
        }
        
        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }
        
        stage('Deploy') {
            steps {
                // Deploy the application to a server
                sh 'scp target/devops.war user@server:/opt/tomcat/webapps'
            }
        }
    }
    
    post {
        always {
            // Clean up workspace
            cleanWs()
        }
    }
}
<<<<<<< HEAD
>>>>>>> f914cc6a238f58ff709a293d6149226e7d50e0c4
=======
>>>>>>> f914cc6a238f58ff709a293d6149226e7d50e0c4
