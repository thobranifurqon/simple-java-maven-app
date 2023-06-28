node {
    withDockerContainer (image:'maven:3.9.0', args:'-v /root/.m2:/root/.m2'){
        stage ('Build') {            
            sh 'mvn -B -DskipTests clean package'
        }
        stage ('Test') {
            sh 'mvn test'
            
        }
        stage ('Deliver') {
            
            sh './jenkins/scripts/deliver.sh'
            
        }
        
    }
}