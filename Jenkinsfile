node {
    withDockerContainer (image:'maven:3.9.0', args:'-v /root/.m2:/root/.m2'){
        stage ('Build') {            
            sh 'mvn -B -DskipTests clean package'
        }
        stage ('Test') {
            sh 'mvn test'
            
        }
        stage('Manual Approval'){
            steps{
                input message: 'Lanjutkan ke tahap Deploy? (klik "Proceed" untuk lanjut ke tahap Deploy)'
            }
        }
        stage ('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            sh 'sleep 60'
        }
        
    }
}