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
        nexusUrl: 'my.nexus.address',
        groupId: 'DEV',
        version: 'V1',
        repository: 'game-of-life-repo',
        credentialsId:'game-of-life-creds'  
        artifacts: 
            [artifactId: 'game-of-life',
             classifier: '',
             file: 'target/game-of-life-v1.war'		,
             type: 'war']
        
     )
}
 }
      }
}

