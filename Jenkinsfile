pipeline{
    agent any
    stages{
        stage('Git Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/preet0807/DevOps.git'

            }
        }

        stage('Unit Testing') {
            steps {
                
                sh 'mvn test'
            }
        }
    }
}
