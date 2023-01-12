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
		sh "hostname -i"
                    }
                }
                stage('linux script') {
                    agent {
                        label "slave"
                    }
                    steps {
                       sh "hostname -i"
                    }
                }
             }
        }
    }
}