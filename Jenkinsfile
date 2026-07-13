pipeline
{
    agent {
         label 'built-in'
    }
    stages
    {
        stage('Download_Master')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('Build_Master')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deployment_Master')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline2/webapp/target/webapp.war ubuntu@172.31.9.45:/var/lib/tomcat10/webapps/test1.war'
            }
        }
        stage('Testing_Master')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline2/testing.jar'
            }
        }
        stage('Delivery_Master')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline2/webapp/target/webapp.war ubuntu@172.31.15.44:/var/lib/tomcat10/webapps/prod1.war'
            }
        }
    
    }
}
