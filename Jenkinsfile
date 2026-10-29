pipeline {
    agent {
        label "node1"
    }
    stages {

        stage('Pull') {
            steps {
                git branch: 'main', url: 'https://github.com/milind55555/Jenkins-Maven-SonarQube-Project.git'
                echo "Pull successful"
            }
        }

        stage('build') {
            steps {
                sh '/opt/apache-maven-3.10.0/bin/mvn package' 
                echo "testing successful"
            }
        }
        stage('Deploy') {
            steps {
                echo "deployment successful"
            }
        }
    }
}
