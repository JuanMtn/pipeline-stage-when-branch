pipeline {
  agent any
  stages{
    stage('Pre-check Queue'){
      steps{
        script{
          waitUntil{
           def queueSize = getQueueSize()
            if(queueSize < mmaxQueueSize){
              return true 
            }else{
              sleep(time:10,unit:'SECONDS')
              return false
            }
          }
        }
      }
    }
    stage("Build Main"){
      when {
        branch 'main' 
      }
      steps {
        echo "Building main" 
      }
    }
    stage("Build Dev"){
          when {
            branch 'dev' 
          }
          steps {
            echo 'Building dev' 
          }
          }
  }
}
