pipeline {
    agent any
    
      environment {
        PATH = "/C:/Program Files/apache-maven-3.9.1-bin/apache-maven-3.9.1:$PATH"
        JAVA_HOME = 'C:/Program Files/Java/jdk-17.0.7'
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
                             -Dsonar.login=sqp_aa61450e90621fb4ed52cb681064649690a71ac5 '
                    }
                }
            }
        }
                stage('Start Prometheus') {
            steps {
                bat 'docker run -d -p 9092:9092 --name prometheus prom/prometheus'
            }
        }

        stage('Create Grafana Dashboard') {
            environment {
                PROMETHEUS_PORT = 9090
                API_KEY = 'eyJrIjoiVzc1R010bUpoYnJFR1FRUHdWVFUwN3U5Skc2TUM2U04iLCJuIjoiSmVua2lucyIsImlkIjoxfQ=='
            }
            steps {
                bat 'docker run -d -p 3001:3000 --name grafana grafana/grafana'
//                 bat 'timeout /t 10 /nobreak'
                bat "curl -X POST -H \"Content-Type: application/json\" \
                    -d '{\"name\":\"db\",\"type\":\"prometheus\",\"url\":\"http://192.168.1.50:9090\",\"access\":\"proxy\",\"isDefault\":true}' \
                    http://admin:${API_KEY}@192.168.1.50:3000/api/datasources"
                bat "curl -X POST -H \"Content-Type: application/json\" \
                    -d '{\"dashboard\":{\"id\":null,\"title\":\"${JOB_NAME}-${BUILD_NUMBER}\",\"tags\":[\"devops\"],\"timezone\":\"browser\",\"schemaVersion\":21,\"panels\":[{\"id\":1,\"gridPos\":{\"x\":0,\"y\":0,\"w\":12,\"h\":8},\"type\":\"graph\",\"title\":\"Panel Title\",\"datasource\":\"db\",\"targets\":[{\"expr\":\"up\",\"legendFormat\":\"\",\"refId\":\"A\"}],\"xaxis\":{\"mode\":\"time\",\"show\":true},\"yaxes\":[{\"format\":\"short\",\"show\":true},{\"format\":\"short\",\"show\":true}]},{\"collapsed\":false,\"gridPos\":{\"h\":2,\"w\":24,\"x\":0,\"y\":8},\"id\":2,\"panels\":[],\"title\":\"\",\"type\":\"row\"}],\"version\":0,\"links\":[]},\"overwrite\":false}' \
                    http://admin:${API_KEY}@192.168.1.50:3000/api/dashboards/db"
            }
        }
    }        
 }




        
