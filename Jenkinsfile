pipeline {
    agent any
    stages {
           stage('Parallel Stage') {
              parallel {
                stage('windows script') {
                    agent {
                        label "master"
                    }
                    steps {
                        	echo "Running in windows agent"
		bat 'echo %PATH%'
                    }
                }
                stage('linux script') {
                    agent {
                        label "slave"
                    }
                    steps {
                       sh "Running in Linux agent"
                    }
                }
             }
        }
    }
}