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

                deploy adapters: [tomcat9(credentialsId: '589632d0-c3f4-4fc0-9261-5e7f8d19ad3a', path: '', url: 'http://172.31.13.241:8080')], contextPath: 'test1', war: '**/*.war' 
                
            }
        }
        
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/vidyasrees/functionaltesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
                
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                
                deploy adapters: [tomcat9(credentialsId: '589632d0-c3f4-4fc0-9261-5e7f8d19ad3a', path: '', url: 'http://172.31.10.80:8080')], contextPath: 'prodapp', war: '**/*.war'
            }    
        }
        
        
        
        
        
        
    }
}
