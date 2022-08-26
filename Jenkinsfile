
pipeline {

agent any 
stages {

stage('Build'){
  steps  {
   
   sh 'make' 
   
  }
  
  }
  stage('Test'){
  steps{
  
  sh 'make check || true' 
 
  }
  
  }   
  stage('Deploy'){
  when{
  
  expression{ 
  currentBuild.result == null || currentBuild.result == 'SUCCESS'
  }
  
  }
  
  steps{
     sh 'Deployed'
  
  
  }
  
  
  
  }
  



}



}



