pipeline
{
    agent any
    stages
    {
        stage('contdownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('contbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('contdeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tom', path: '', url: 'http://3.90.26.151:8080')], contextPath: 'testapp1', war: '**/*.war'
            }
        }
        stage('conttesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('contdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tom', path: '', url: 'http://98.93.61.56:8080')], contextPath: 'prodapp1', war: '**/*.war'
            }
        }
    }
}
