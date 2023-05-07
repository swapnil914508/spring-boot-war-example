pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('SCM checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sudhakarbastawade2303/spring-boot-war-example.git']])
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Deploy to test env') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat_server', path: '', url: 'http://65.0.139.27:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
}


