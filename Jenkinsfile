pipeline {

    agent any
    triggers {
        pollSCM('* * * * *') //polling for changes, here once a minute
    }

    

    stages {


        stage('build') {
            steps {
                script {
                   sh './gradlew build' //Running our first build
                }
                
            }
        }

        /* stage('Compile') {
            steps {
                script {
                   sh './gradlew clean compile --no-daemon'
                }
                
            }
        } */

        stage('Unit & Integration Tests') {
            steps {
                script {
                    try {
                        sh './gradlew clean test --no-daemon' //run a gradle task
                    } finally {
                        junit '**/build/test-results/test/*.xml' //make the junit test results available in any case (success & failure)
                    }
                }
            }
        }
    }
}