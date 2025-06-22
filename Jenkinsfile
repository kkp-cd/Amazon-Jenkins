pipeline {
    agent any
    //environment {
        // Use PATH+EXTRA to append to PATH properly
       // PATH = "/usr/bin:/bin:/opt/homebrew/bin"
    
    stages {

        stage('pull data') {
            steps {
                git branch: 'dev', url: 'https://github.com/kkp-cd/Amazon-Jenkins.git'
            }
        }
        stage('compile_dev') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('build_dev') {
            steps {
                 sh 'mvn clean install'
            }
        }
    }

  post {
  success{
     echo 'Build success'
  }
    failure{
       echo 'Failure in the build'
   }
  }
}
