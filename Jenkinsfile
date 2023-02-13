pipeline 
{
    agent any

    stages 
    {
        stage('SCM') 
        {
            steps 
            {
                git 'https://github.com/vijaykrishnakp1/maven.git'
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
               sh 'sudo cp -pvr /var/lib/jenkins/workspace/Sample-Pipeline/webapp/target/webapp.war /var/lib/tomacat9/webapps'
            }
        }
    }
    post
    {

    	always
    	{
    	emailext body: '''Hi,
Please find the summary
$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:

Check console output at $BUILD_URL to view the results.
Thanks & Regards 
vijay krishna''', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: 'vijaykrishnakp7@gmail.com'
    	}

    }
}
         

