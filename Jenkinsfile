pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Pulling code from GitHub..."
                checkout scm
            }
        }

        stage('Prepare Target Folder') {
            steps {
                script {
                    sh 'mkdir -p copied_html'
                }
            }
        }

        stage('Copy File') {
            steps {
                script {
                    sh 'cp index.html copied_html/'
                }
            }
        }

        stage('Archive Result') {
            steps {
                archiveArtifacts artifacts: 'copied_html/index.html', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully."
        }
    }
}
