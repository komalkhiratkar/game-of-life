pipeline {
    agent any
      tools {
          jdk 'java-8'
          maven 'maven-3'
      }
      stages {
          stage ('clone') {
              steps {
                  git 'https://github.com/komalkhiratkar/game-of-life.git'
              }
          }
          stage ('test') {
              steps {
                  echo 'running test cases'
              }
          }
          stage ('build') {
              steps {
                  sh 'mvn package'
              }
          }
         stage ('nexus artifact uploader'){
            steps {
     nexusArtifactUploader(
        nexusVersion: 'nexus3',
        protocol: 'http',
        nexusUrl: '172.31.8.147:8081',
        groupId: 'DEV',
        version: '$BUILD_NUMBER',
        repository: 'game-of-life-repo',
        credentialsId: 'game-of-life-creds',
        artifacts: [
            [artifactId: 'gameoflife',
             classifier: '', 
             file:'gameoflife-web/target/gameoflife.war',
             type: 'war']
     ]   
     )
  
     }     
    }
        
      stage ('deploy to tomcat'){
        steps {

   deploy adapters: [tomcat8(credentialsId: 'tomcatcreds', path: '', url: 'http://172.31.3.167:8080')], contextPath: 'game-of-life --2', war: 'gameoflife-web/target/gameoflife.war'
}
 }
 
      }
}

