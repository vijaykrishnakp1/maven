pipeline 
{
    agent any

    stages 
    {
        stage('Build') 
        {
            steps 
            {
                git credentialsId: '5f8ff449-f742-424e-a39a-0ef758dac005', url: 'https://github.com/vijaykrishnakp1/vijay-50.git'
            }
        }

        stage('Test') 
        {
            steps 
            {
               sh 'mvn package'
            }
        }
    }
    post
    {

    	always
    	{
    		  emailext body: '''Hi,
please find the summary
$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:
Check console output at $BUILD_URL to view the results.
Thanks
Devops Team''', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: 'vijaykrishnakp7@gmail.com'
    	}

    }
}
         

