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
         
        
   
 
      }
}

