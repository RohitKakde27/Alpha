pipeline {
     agent any
     tools {
        maven 'mymaven'
        jdk 'myjava' 
            }
     
     stages {
        
        stage('Pull') {
              steps {
                 echo ' pulling code '
                 git branch: 'main', url: 'https://github.com/RohitKakde27/Alpha.git'
              }
         }

        stage('Build') {
              steps {
                 echo "Build stage is running"
                 sh'mvn clean package'
              }
         }
        
        stage('Test') {
              steps {
                 echo "Testing artifect stage is running"
                 sh """
                        mvn sonar:sonar \
                         -Dsonar.projectKey=project \
                         -Dsonar.host.url=http://43.205.135.117:9000 \
                         -Dsonar.login=91c8616c0c3f4f1482e233027d42e5e58341123a
                    """
              }
         }
        
        stage('Deploy') {
              steps{
                sshagent(['tomy']) {
                    
                    echo "Deployment stage is running"
                    sh """
                        scp -o StrictHostKeyChecking=no target/studentapp-2.2-SNAPSHOT.war  centos@172.31.42.231:/opt/apache-tomcat-8.5.84/webapps/
                        ssh centos@172.31.42.231 /opt/apache-tomcat-8.5.84/bin/shutdown.sh
                        ssh centos@172.31.42.231 /opt/apache-tomcat-8.5.84/bin/startup.sh
                 """
              
                }
              }
         }
        
     }
}