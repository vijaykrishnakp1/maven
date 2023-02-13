pipeline 
{
    agent any

    stages 
    {
        stage('SCM') 
        {
            steps 
            {
                git credentialsId: '5f8ff449-f742-424e-a39a-0ef758dac005', url: 'https://github.com/vijaykrishnakp1/maven.git'
            }
        }

        stage('Build') 
        {
            steps 
            {
               sh 'mvn package'
            }
        }
        stage('Deploy') 
        {
            steps 
            {
               sh 'cp /var/lib/jenkins/workspace/Sample-Pipeline/webapp/target/webapp.war /var/lib/tomacat9/webapps/'
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
         

