pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package' // build the project using maven
                echo 'Build stage successful'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' // run unit tests using maven
                echo 'Test stage successful'
                post{
                    always{
                        junit 'target/surefire-reports/*.xml'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn deploy' // deploy the built artifact to a repository using maven
                echo 'Deployment successful'
            }
        }
    }
    post{
        failure{
            echo 'Pipeline failed'
        }
    }
}
