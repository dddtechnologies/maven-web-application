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
   }
}
