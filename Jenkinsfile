pipeline {
    agent {
        label 'maven'
    }
    environment {
        PATH = "$PATH:/opt/maven/bin"
    }
    stages {

       stage("build"){
        steps {
            echo "------- build started --------"
            sh 'mvn clean deploy -Dmaven.test.skip=true'
            echo "---------build completed ----------"
        }
       
    }
    stage("test"){
        steps{
            echo "--------unit test started ---------"
            sh 'mvn surefire-report:report'
            echo "---------unit test completed -------"
        }
    }
    stage('SonarQube analysis'){
    environment {
      scannerHome = tool 'sonar-server' //sonar scanner name should be same as what we have defined in the tools
    }
    steps {                                 // in the steps we are adding our sonar cube server that is with Sonar Cube environment.
    withSonarQubeEnv('nithi-sonarqube-server') {
       sh "${scannerHome}/bin/sonar-scanner" // This is going to communicate with our sonar cube server and send the analysis report.
        }
      }
    }
    
    stage("Quality Gate") {
        steps {
            script {
            timeout(time: 1, unit: 'HOURS') {
                def qg = waitForQualityGate()
                if (qg.status != 'OK') {
                    error " Pipeline aborted due to quality gate failure: ${qg.status}"
                }
            }
        }
    }
}
}
}
