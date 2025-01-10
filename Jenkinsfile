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

                 sh 'scp /var/lib/jenkins/workspace/DescriptivePipeline/webapp/target/webapp.war ubuntu@172.31.44.74:/var/lib/tomcat10/webapps/testapp.war'
                
            }
        }
        
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/vidyasrees/functionaltesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DescriptivePipeline/testing.jar'
                
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '4b28a9ed-422f-45fe-84d9-00972591d91e', path: '', url: 'http://172.31.39.206:8080')], contextPath: 'prod1', war: '**/*.war'
            }    
        }
        
        
        
        
        
        
    }
}
