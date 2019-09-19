#!/groovy

pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /Users/tang/.m2:/root/.m2'
        }
    }
    stages {
        stage('Init') {
            steps{
                wrap([$class: 'BuildUser']) {
                    def userid = ${env.BUILD_USER}
                    currentBuild.displayName = "${WorkItemID}"  + "_" + "${BUILD_NUMBER}" + " by " + "${userid}"
                }
            }
        }
        stage('Print Parameters'){
            steps {
                sh 'echo `pwd`'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
