// Jenkinsfile (Declarative Pipeline)
pipeline {
//     agent any
    agent { docker { image 'maven:3.3.3' } }

     environment {
            USERNAME     = credentials('root')
            PASSWORD = credentials('123123')
        }

    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
                sh ' echo "hello jenkins"'
                sh 'echo ${USERNAME} ------  ${PASSWORD}'
            }
        }
    }
        post {
            always {
                echo 'This will always run'
            }
            success {
                echo 'This will run only if successful'
            }
            failure {
                echo 'This will run only if failed'
            }
            unstable {
                echo 'This will run only if the run was marked as unstable'
            }
            changed {
                echo 'This will run only if the state of the Pipeline has changed'
                echo 'For example, if the Pipeline was previously failing but is now successful'
            }
        }

}
