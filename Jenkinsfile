pipeline {
    agent any

    tools {
        jdk 'JDK11'
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'Main',
                    url: 'https://github.com/AbhijnaGowda3/practice1.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'nohup java -jar target/MyMavenApp-1.0-SNAPSHOT.jar > app.log 2>&1 &'
            }
        }
    }

    post {

        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
