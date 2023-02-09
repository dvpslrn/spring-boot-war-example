pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        
        stage('scm checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sudhakarbastawade2303/spring-boot-war-example.git']]) 
            }
        }
        stage('build the scm') {
            steps {
                sh 'mvn install'
            }
        }
        stage('deploy to tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat_server', path: '', url: 'http://13.234.77.239:8080/')], contextPath: '/app', war: '*/.war'
            }
        }
    }
}
