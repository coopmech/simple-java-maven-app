node {
     docker {
         image 'maven:3-alpine'
         args '-v /root/.m2:/root/.m2'
     }
     stage('Build') {
         sh 'mvn -B -DskipTests clean package'
     }
     stage('Test') {
         sh 'mvn test'
     }
     post {
         always {
             junit 'target/surefire-reports/*.xml'
             }
          }
     stage('Deliver') {
         sh './jenkins/scripts/deliver.sh'
     }
}
