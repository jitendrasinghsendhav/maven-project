pipeline {
   agent any
   stages{
        stage('build'){
            steps{
            sh 'mvn clean package'
            sh 'docker stop $( docker ps -q)'
            sh 'if [ `docker ps -q | wc -l `  -gt 0 ] ;then docker stop $( docker ps -q) ; else echo "zaho"; fi'
            sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            sh "docker run -d -p 8181:8080 tomcatwebapp:${env.BUILD_ID}  "

           
            }
        }
   }
 }
