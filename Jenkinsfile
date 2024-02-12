pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/Ramesh9949/pollscm.git'
            }
        }
        stage('Continuousbuild')
        {
            steps
            {
                sh 'mvn clean package'
            }
        }
         stage('Continuousdeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '9a4e0403-23c8-463e-9cad-778e9d428803', path: '', url: 'http://172.31.20.66:8080')], contextPath: 'bhav', war: '**/*.war'
            }
        }
         stage('Continuoustesting')
        {
            steps
            {
                git 'https://github.com/Ramesh9949/FunctionalTesting.git'
                
                sh 'java -jar /var/lib/jenkins/workspace/ramesh/testing.jar'
            }
        }
        stage('Continuousdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '450cfb8b-82e7-4ea4-b8cf-1cd08ad0b9aa', path: '', url: 'http://172.31.20.66:8080')], contextPath: 'app', war: '**/*.war'
            }
        }
        
    }
    
}    
