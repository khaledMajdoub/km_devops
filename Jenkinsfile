pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage ('Checkout to SCM') {
            steps {
                git branch: 'khaled', credentialsId: 'devops_khaled', url: 'https://github.com/KhaledMajdoub1/km_devops.git'
                sh 'git checkout khaled'
                sh 'ls -la'
                sh "echo 'Hello World'"
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarInstallation') {
                    sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=devops_km -Dsonar.projectName=\'devops_km\' -Dsonar.projectVersion=1.0  -Dsonar.sources=src/main/java -Dsonar.sourceEncoding=UTF-8 -Dsonar.language=java -Dsonar.java.binaries=target/classes'
                }
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
        // stage ('JUNIT/MOCKITO') {
        //     steps {
        //     }
        // }
        stage ('Deploy to Nexus') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}