pipeline {
  agent any
    stages{
      stage('One'){
        steps{
          echo 'THis is stage 1'
        }
      }
      stage('Two'){
        steps{
          echo 'This is stage 2'
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
