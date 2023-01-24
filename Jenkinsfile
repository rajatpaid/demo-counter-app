pipeline{
    
	agent any

    	 tools {
            maven 'mvn'
                }

	stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/rajatpaid/demo-counter-app.git'
                }
            }
        }
        stage('UNIT testing'){

            steps{

         	sh 'mvn test'
            }
        }
	
	stage('Integration Test'){

            steps{

                sh 'mvn verify -DskipUnitTests'
            }
        }
	stage('Maven Build'){

            steps{
                  
                
 		sh 'mvn clean install'
		
            }
        }
         stage('Sonarqube Analysis'){

            steps{
		script{

                withSonarQubeEnv(credentialsId: 'sonar') {
    		sh 'mvn clean package sonar:sonar'
		}

            }
		}
        }



        
        }
        
}
