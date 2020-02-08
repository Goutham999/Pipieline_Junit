pipeline {
  agent any
  
  tools{
    maven "Maven3.6.3"
  }
    stages{
      stage('One'){
        steps{
          echo 'THis is stage 1'
          bat "mvn clean package"
          bat "cd target"
          bat "java -jar SampleCode.jar"
          
        }
        post {
          success{
            junit '**/target/surefire-reports/*.xml'
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
