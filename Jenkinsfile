pipeline {
  agent any
  
  tools{
    maven "Maven3.6.3"
  }
    stages{
      stage('One'){
        steps{
          echo 'THis is stage 1'
          git 'https://github.com/balaatgithub1/sample-code-java.git'
          bat "mvn package"
          bat "cd target"
          
        }
        post {
          success{
            junit '**/target/surefire-reports/*.xml'
          }
        }
      }
      stage('Two'){
        steps{
          echo 'This is stage 2'
          step([$class: 'JUnitResultArchiver', testResults: 'target/surefire-reports/*.xml'])
        }
      }

      stage('Three'){
        parallel{
          stage('Three.A'){
            steps{
              echo 'THis is stage 3.A'
            }
          }
          stage('Three.B'){
            steps{
              echo 'This is stage 3.B'
            }
          }
        }
      }
    }
}
