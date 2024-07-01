pipeline {
	agent {label 'maven'}

	stages {
		stage("build"){
			steps{
				echo "-------------build started-----------"
				sh 'mvn clean deploy -Dmaven.test.skip=true'
				echo "------------build completed----------"
			}

		}
		stage("test"){
			steps{
				echo "-------------unit test started-----------"
				sh 'mvn surefire-report:report'
				echo "------------unit test completed----------"
			}
		}

    }
}
