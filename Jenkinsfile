pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Default Maven'
    }

    environment {
        IMAGE_NAME = 'manujanaa/habit-tracker'
        SONAR_PROJECT_KEY = 'habit-tracker'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                sh 'mvn clean verify'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        mvn sonar:sonar \
                        -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                        -Dsonar.projectName=habit-tracker
                    '''
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                    docker build \
                    -t ${IMAGE_NAME}:${BUILD_NUMBER} \
                    -t ${IMAGE_NAME}:latest .
                '''
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
                  testResults: 'target/surefire-reports/*.xml'

            archiveArtifacts artifacts: 'target/*.jar',
                             allowEmptyArchive: true
        }

        success {
            echo 'Habit Tracker CI pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the stage logs.'
        }
    }
}
