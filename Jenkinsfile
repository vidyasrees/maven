pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/vidyasrees/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline-SCP/webapp/target/webapp.war ubuntu@172.31.5.63:/var/lib/tomcat9/webapps/testapp.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/vidyasrees/functionaltesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline-SCP/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline-SCP/webapp/target/webapp.war ubuntu@172.31.3.151:/var/lib/tomcat9/webapps/prodapp.war'
            }
        }
        
    }
}
