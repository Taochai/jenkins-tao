// // Jenkinsfile (Declarative Pipeline)
// pipeline {
//     agent any
// //     agent { docker { image 'maven:3.3.3' } }
//
// //      environment {
// //             USERNAME_TEST     = credentials('root')
// //             PASSWORD_TEST     = credentials('vagrant')
// //         }
//      environment {
//              AWS_ACCESS_KEY_ID     = 'jenkins-aws-secret-key-id'
//              AWS_SECRET_ACCESS_KEY = 'jenkins-aws-secret-access-key'
//          }
//
//     stages {
//         stage('build') {
//             steps {
//                 sh 'ls -al ./'
//                 sh ' echo "hello jenkins"'
//                 sh 'echo ${AWS_ACCESS_KEY_ID} ------  ${AWS_SECRET_ACCESS_KEY}'
//             }
//         }
//           stage('Gradle Build') {
//                     steps {
//                         sh './gradlew build'
//                     }
//                 }
//                 stage('Gradle Test') {
//                     steps {
//                         sh './gradlew check'
//                     }
//                 }
//     }
//         post {
// //             always {
// //                 echo 'This will always run'
// //             }
// //             success {
// //                 echo 'This will run only if successful'
// //             }
// //             failure {
// //                 echo 'This will run only if failed'
// //             }
// //             unstable {
// //                 echo 'This will run only if the run was marked as unstable'
// //             }
// //             changed {
// //                 echo 'This will run only if the state of the Pipeline has changed'
// //                 echo 'For example, if the Pipeline was previously failing but is now successful'
// //             }
//                 always {
//                         archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
//                         junit 'build/reports/**/*.xml'
//                     }
//         }
//
// }
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew check'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
    }
}
