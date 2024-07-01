pipeline {
    agent {label 'maven'}
pipeline {
    agent {
        label 'maven'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy -Dmaven.test.skip=true'
            }
        }
    }
}
