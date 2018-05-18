
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'set'
            }
        }
    }
    
    post {
        always {
            echo 'This will always run'
            
            slackSend channel: '#general',
                color: 'good',
                message: "The pipeline ${currentBuild.fullDisplayName} completed a build."
            
            mail to: 'jflopezfernandez@gmail.com',
                subject: "Build Complete: ${currentBuild.fullDisplayName}",
                body: "${env.BUILD_URL}"
        }
        
        sucess {
            echo 'This will only run if successful'
        }
        
        failure {
            echo 'This will run only if failed'
        }
        
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        
        changed {
            echo 'This will run only if the state of the pipeline has changed'
            echo 'For example, if the pipeline was previously failing and is now successful'
        }
    }
}
