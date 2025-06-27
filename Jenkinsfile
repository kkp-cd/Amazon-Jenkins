pipeline {
    agent any
    //environment {
        // Use PATH+EXTRA to append to PATH properly
        // PATH = "/usr/bin:/bin:/opt/homebrew/bin"
    stages {
        stage('pull') {
            steps {
                git branch: 'main', url: 'https://github.com/kkp-cd/Amazon-Jenkins.git'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('build') {
            steps {
                 sh 'mvn clean install'
            }
        }
      }

    post {
        success {
            emailext(
                to: 'kiran29822k8@gmail.com',
                subject: "✅ SUCCESS: Job '${env.JOB_NAME} [#${env.BUILD_NUMBER}]'",
                body: """<p>Good news! The job <b>${env.JOB_NAME}</b> succeeded.</p>
                         <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>""",
                mimeType: 'text/html'
            )
        }

        failure {
            emailext(
                to: 'kiran29822k8@gmail.com',
                subject: "❌ FAILURE: Job '${env.JOB_NAME} [#${env.BUILD_NUMBER}]'",
                body: """<p>Unfortunately, the job <b>${env.JOB_NAME}</b> failed.</p>
                         <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>""",
                mimeType: 'text/html'
            )
        }
        always {
            echo "Build complete"
        }
    }
}
