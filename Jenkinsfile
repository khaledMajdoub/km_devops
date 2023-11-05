pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage ('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/khaled']], extensions: [cleanAfterCheckout(deleteUntrackedNestedRepositories: true), cleanBeforeCheckout(deleteUntrackedNestedRepositories: true)], userRemoteConfigs: [[credentialsId: 'devops_khaled', url: 'https://github.com/KhaledMajdoub1/km_devops.git']])
                sh 'git checkout khaled'
                sh 'ls -la'
                sh "echo 'Hello World'"
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarInstallation') {
                    sh 'mvn clean sonar:sonar -Dsonar.projectKey=devops_km -Dsonar.projectName=\'devops_km\''
                }
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn --version'
            }
        }
        // stage ('Deploy') {
        //     steps {
        //     }
        // }
    }
}