pipeline {
  agent any
    stages{
      stage('One'){
        steps{
          echo 'THis is stage 1'
          sh "mvn package"
          bat label: '', script: ''' cd target
              java -jar SampleCode.jar'''
          
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
