node('built-in') {
    
    stage('continuousDownload')
    {
    
        git 'https://github.com/Ramesh9949/pollscm.git'
    }
    stage('continuousbuild')
    {
    
        sh 'mvn clean package'
    }
    stage('continuousdeployment')
    {
    
        deploy adapters: [tomcat9(credentialsId: '450cfb8b-82e7-4ea4-b8cf-1cd08ad0b9aa', path: '', url: 'http://172.31.20.66:8080')], contextPath: 'app', war: '**/*.war'
    }
    stage('continuoustesting')
    {
    
        git 'https://github.com/Ramesh9949/FunctionalTesting.git'
        
        sh 'java -jar /var/lib/jenkins/workspace/bhavya/testing.jar'
    }
     stage('continuousdelivery')
    {
    
        deploy adapters: [tomcat9(credentialsId: '450cfb8b-82e7-4ea4-b8cf-1cd08ad0b9aa', path: '', url: 'http://172.31.20.66:8080')], contextPath: 'ram', war: '**/*.war'
    }
    
}         
