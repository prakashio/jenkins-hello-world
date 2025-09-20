pipeline {
    agent any

    tools {
        maven 'M3911'
    }

    stages {
        stage ('Maven Version Check') {
            steps {
                sh 'mvn -v'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh "mvn clean package -DskipTests=true"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh "mvn test"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh "java -jar target/hello-demo-*.jar "
            }
        }
        stage("Health Check") {
            steps{
                echo 'Health Check...'
                sh "curl -s http://localhost:6767/hello"
            }
        }
    }
}