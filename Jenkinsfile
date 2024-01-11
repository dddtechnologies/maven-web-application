/*
node 
{

def mavenHome = tool name: "maven3.9.6"

stage ('checkout')
{
git branch: 'main', credentialsId: '987a3773-624b-4ccd-a30d-a246ae929c97', url: 'https://github.com/dddtechnologies/maven-web-application.git'
}

stage ('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}


stage ('ExecuteSonarQubeReport')
{
    sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ('uploadartifact')
{
    sh "${mavenHome}/bin/mvn deploy"
}

stage ('Tomcat deployment')
{
    sshagent(['bfa36316-9f82-434a-9e34-bf3ae7409ec0']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war  ec2-user@100.25.142.238:/opt/apache-tomcat-9.0.83/webapps"     
}   
}


stage('email notification')
{
    emailext body: 'The jenkins pipeline for wallmart-dev-sample1 is success', subject: 'Build is success', to: 'dddreamtechnologies@gmail.com'    
}    
}
*/


pipeline {
    agent any

    tools {
        maven "maven3.9.6"
    }
    
    stages {
        
            stage('git clone') {
                steps {
                    git branch: 'main', credentialsId: '987a3773-624b-4ccd-a30d-a246ae929c97', url: 'https://github.com/dddtechnologies/maven-web-application.git'
                }
            }
        
            stage('maven build'){
                steps {
                    sh "mvn clean package"
                }
            }
        
            stage('sonarqubereport'){
                steps {
                    sh "mvn sonar:sonar"
                }
            }
        
            stage ('Upload artifact to nexus'){
                steps {
                    sh "mvn deploy"
                }
            }
    }
}
