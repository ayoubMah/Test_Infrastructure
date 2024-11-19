pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'git@github.com:ayoubMah/Test_Infrastructure.git'
            }
        }
        stage('Build Backend') {
            steps {
                dir('Demo1ForDev') {
                    sh 'mvn clean package'
                }
            }
        }
        stage('Deploy Backend') {
            steps {
                sh 'scp Demo1ForDev/target/Demo1ForDev-1.0-SNAPSHOT.jar back@192.168.0.10:/dev/backend.jar'
            }
        }
        stage('Deploy Frontend') {
            steps {
                sh 'scp -r FrontEndForDemo1ForDev/* front@192.168.0.12:/dev/frontend/'
            }
        }
    }
}
