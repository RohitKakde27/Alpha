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
                 sh'maven clean package'
              }
         }
        
        stage('Test') {
              steps {
                 echo "Build stage is running"
              }
         }
        
        stage('Deploy') {
              steps {
                 echo "Build stage is running"
              }
         }
        
     }
}