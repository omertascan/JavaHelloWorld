pipeline {

agent any 
stages {

stage('Build'){
  steps  {
    mkfile_path := $(abspath $(lastword $(MAKEFILE_LIST)))
    mkfile_dir := $(dir $(mkfile_path))
   sh 'make' 
   archiveArtifacts artifacts: ' **/target/*.jar  ', fingerprint:true 
  }
  
  }
  stage('Test'){
  steps{
  
  sh 'make check || true' 
  junit '  **/target/*.xml  ' 
  }
  
  }   
  stage('Deploy'){
  when{
  
  expression{ 
  currentBuild.result == null || currentBuild.result == 'SUCCESS'
  }
  
  }
  
  steps{
     sh 'make publish'
  
  
  }
  
  
  
  }
  



}



}



