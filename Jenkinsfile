pipeline {
  agent any
  tools {
    maven 'Maven-3.6.3'
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://192.168.1.56:8090')], contextPath: '/pipeline', onFailure: false, war: 'target/*.war'
        }
      }
    }
  }
}