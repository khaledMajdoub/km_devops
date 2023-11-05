pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage ('Checkout') {
            steps {
                git branch: 'khaled', url: 'https://github.com/KhaledMajdoub1/km_devops.git'
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage ('Deploy') {
            steps {
            }
        }
    }
}