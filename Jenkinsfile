pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/${branch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '41921dde-34dd-4183-8ba1-2b7179246052', url: 'git@github.com:wzcwuwh/tomcat-webapp-demo.git']]])
            }
        }
        stage('build project') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('publish project') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '4ca413e3-5ecc-4261-8ea9-8194be0428fc', path: '', url: 'http://9.197.8.167:8888/')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
