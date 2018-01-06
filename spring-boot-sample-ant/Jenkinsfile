pipeline {
//     agent { label 'docker-agent' }
     agent any
     stages {
          stage('Checkout') {
               steps {
                    git credentialsId: 'gitlab', url: 'http://192.168.33.11/root/pipeline-net'
               }
          }
          stage('Second Stage') {
               steps {
                    sh 'ant -v -Drevision=1.5.9.RELEASE -f spring-boot-sample-ant/build.xml'
                    echo 'Step 3. Third time Hello'
               }
          }
     }
}
