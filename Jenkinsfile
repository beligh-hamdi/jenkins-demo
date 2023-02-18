pipeline {
    agent { label 'built-in' }
    tools {
        jdk: 'OpenJDK17'
    }
    stages {
        
        stage("Clone the project") {
            git branch: 'main', url: 'https://github.com/beligh-hamdi/jenkins-demo.git'
        }

        stage("Compilation") {
            sh "./mvnw clean install -DskipTests"
        }

        stage("Tests and Deployment") {
            stage("Runing unit tests") {
                sh "./mvnw test -Punit"
            }
            stage("Deployment") {
                sh 'nohup ./mvnw spring-boot:run -Dserver.port=8001 &'
            }
        }
    }
 
}
