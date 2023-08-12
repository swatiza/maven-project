pipeline
{ 
agent any
stages{
  stage('print hi')
  { steps {  sh 'echo hi' } }
  
  stage ('execute unit and component test')  //common stage
{parallel                                       //jenkins will execute below stages parallely
   { stage ('execute unit test')
     {steps { sh 'echo execute_unit_test'  }} 

    stage ('execute component test')
     { steps { sh 'echo execute_componet_test' } } 
  }

 }

}
}
