pipeline {
    agent any
 
    stages {
        stage('Clone') {
            steps {
              git credentialsId: 'GITHUB', url: 'https://github.com/meghavathveeresh/shopping-cart.git'
            }
        }
          stage('Build') {
            steps {
               bat 'mvn clean install'
            }
        }
         
          stage('Generate Artifacts') {
            steps {
               archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
		stage('deploy') {
            steps {
              deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'AMDN', path: '', url: 'http://localhost:8080/')], contextPath: 'shopping mall', war: 'target/*.war'
			  
                    }
				   
			      }
			    }
			 }
 