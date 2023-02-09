pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        
        stage('scm checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/dvpslrn/spring-boot-war-example.git']]) 
            }
        }
        stage('build the scm') {
            steps {
                sh 'mvn install'
            }
        }
        stage('deploy to tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://43.205.192.136:8080/')], contextPath: '/app/', war: '*/.war'
            }
        }
    }
}
