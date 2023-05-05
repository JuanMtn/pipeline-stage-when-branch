pipeline {
  agent any;
  def maxQueueSize=5;
  def getQueueSize(){
   def queue=jenkins.instance.queue
   def items =queue.items
    return items.size()
  }
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
