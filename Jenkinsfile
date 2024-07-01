pipeline {
    agent {lable 'maven'}
    environment {
        PATH = "$PATH:/opt/maven/bin"
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy -Dmaven.test.skip=true'
            }
        }
    }
}
