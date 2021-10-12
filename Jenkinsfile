pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'url: https://github.com/Hithesh13295/maven-helloworld.git'

                // Run Maven on a Unix agent.
                sh "/usr/share/maven/bin/mvn clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
            stage('Deploy') {
                steps {
             deploy adapters: [tomcat8(credentialsId: '9422bac5-6fba-48d1-82ea-9ef34eefa8d1', path: '', url: 'http://localhost:9090/')], contextPath: 'webapp', war: '**/*.war'       
                }
            }
    }
}
