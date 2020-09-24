pipeline {
   agent any
   stages {
        stage('pull code') {
           steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'sdsd', url: 'https://github.com/tian1029/test.git']]])
           }
        }
        stage('build project') {
           steps {
              sh 'mvn clean package  -Dmaven.test.skip=true'
           }
        }
        stage('publish project') {
           steps {
              deploy adapters: [tomcat8(credentialsId: 't8', path: '', url: 'http://172.16.18.80:8082/')], contextPath: null, war: 'target/*.war'

           }
        }

   }

}