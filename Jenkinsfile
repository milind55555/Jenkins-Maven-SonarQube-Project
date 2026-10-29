
pipeline {
    agent {
        label 'node1'
    }

    stages {
        stage('Pull') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/milind55555/Jenkins-Maven-SonarQube-Project.git'

                echo 'Pull successful'
            }
        }

        stage('Build and Test') {
            steps {
                sh '''
                    /opt/apache-maven-3.10.0/bin/mvn clean verify
                '''
            }
            post {
                always {
                    junit testResults: '**/target/surefire-reports/TEST-*.xml',
                          allowEmptyResults: true
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv(
                    installationName: 'sonar-server',
                    credentialsId: 'sonar-token'
                ) {
                    sh '''
                        /opt/apache-maven-3.10.0/bin/mvn \
                          org.sonarsource.scanner.maven:sonar-maven-plugin:sonar \
                          -Dsonar.projectKey=sonar-project
                    '''
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Build and SonarQube analysis completed'
                echo 'Add your actual deployment commands here'
            }
        }
    }
}
