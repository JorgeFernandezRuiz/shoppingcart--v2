pipeline {
    agent any
    parameters {
        booleanParam(name: "RUN_INTEGRATION_TESTS", defaultValue: true)
    }
    stages{
        stage('Test'){
            parallel{
                stage('Unit Tests'){
                    sh './mvnw test -D testGroups=unit'
                }
                stage('Integration Tests'){
                    when {
                       expression { return params.RUN_INTEGRATION_TESTS }
                    }
                    sh './mvnw test -D testGroups=integration'
                }
            }
        }
    }
}