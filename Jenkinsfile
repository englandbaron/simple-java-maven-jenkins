#!/groovy

// pipeline {
//     // agent {
//     //     docker {
//     //         image 'maven:3-alpine'
//     //         args '-v /Users/tang/.m2:/root/.m2'
//     //     }
//     // }
//     agent { node { label 'master' } }
//     stages {
//         stage('Init') {
//             steps{
//                 script{
//                     wrap([$class: 'BuildUser']) {
//                         def userid = env.BUILD_USER
//                         currentBuild.displayName = "${WorkItemID}"  + "_" + "${BUILD_NUMBER}" + " by " + "${userid}"
//                     }
//                 }
//             }
//         }
//         stage('Print Parameters'){
//             steps {
//                 script{
//                     sh 'echo `pwd`'
//                 }
//             }
//         }
//     }
// }
stage("Print Hello world"){
    node('master'){
        wrap([$class: 'BuildUser']) {
            def userid = env.BUILD_USER
            currentBuild.displayName = "${WorkItemID}"  + "_" + "${BUILD_NUMBER}" + " by " + "${userid}"
        }
    }

    node('master'){
        sh "echo `pwd`"
    }
}