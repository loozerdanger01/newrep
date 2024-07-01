pipeline {
	agent {label 'maven'}

	stages {
		stage("build"){
			steps{
				echo "-------------build started-----------"
				sh 'mvn clean deploy'
				echo "------------build completed----------"
			}

		}
		

    }
}
