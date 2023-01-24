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
		-D sonar.projectKey=cicd-project \
  		-D sonar.host.url=http://3.110.218.25:9000 \
    		-D sonar.login=sqp_0f0c395f5b920dbb3b735c8da78fd299afaac9ef
	}

            }
		}
        }



        
        }
        
}
