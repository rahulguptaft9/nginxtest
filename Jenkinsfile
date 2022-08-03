pipeline {
    
	  agent any
  	  tools {nodejs "node"}

	environment{
	registry="mrchelsea/dockertest"
	registryCredential='dockerhub'
	dockerImage=''
	}
	stages{
	stage('Git') {
		steps{
		git 'https://github.com/rahulguptaft9/nginxtest'
		}	
	}
  	stage('Building Image') {
		steps{
			script{
			 	dockerImage=docker.build registry	
			}
		}
	}
	stage('Registring Image') {
		steps{
			script{
				docker.withRegistry('',registryCredential){
				dockerImage.push()
				}
			}
		}
	}
  
  
  }
  }
