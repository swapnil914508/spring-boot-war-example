pipeline {
    agent any
    
    tools {
        maven 'M2_HOME'
    }

    stages {
        stage('git-checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sudhakarbastawade2303/spring-boot-war-example.git']])
            }
        }
        stage('building-source-code') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy-to-tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat9', path: '', url: 'http://44.211.150.240:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
}

