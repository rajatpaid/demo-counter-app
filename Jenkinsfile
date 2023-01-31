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


        
        }
        
}
