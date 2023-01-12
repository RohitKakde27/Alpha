pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
	agent {
           label 'slave'
       }
      stages{
           stage('pull'){
               steps{
		 echo 'cloning..'
                 git branch: 'main', url: 'https://github.com/RohitKakde27/Alpha.git'
              }
          }
          stage('Build'){
              steps{
                  echo 'Code-Build..'
                  sh 'mvn compile'
                  sh 'hostname -i'
	      }
          }
          stage('Package'){
              steps{
                  sh 'mvn package'
              }
          }
          stage('deploy-dev'){
              steps{
                  sshagent(['tomcat-1']) {
    // some block

                          sh """
                          scp -o StrictHostKeyChecking=no target/studentapp-2.2-SNAPSHOT.war centos@172.31.42.231:/opt/apache-tomcat-8.5.84/webapps/
                          
                          ssh centos@172.31.42.231:/opt/apache-tomcat-8.5.84/bin/shutdown.sh
                          
                          ssh centos@172.31.42.231:/opt/apache-tomcat-8.5.84/bin/startup.sh
                      
                      """
                }
              }
              }
          }
      }

