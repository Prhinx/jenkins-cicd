pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
            echo 'Building..'
                sh 'mvn clean package'
            }
        }
        stage('test') {
            steps {
            echo 'Building..'
                sh 'mvn test'
            }
        }
        stage('deploy') {
            steps {
            echo 'Deploying....' 
            sshagent(['deploy']) { 
                sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Jenkins-CICD-Project/target/webapp-0.2.war centos@18.208.206.41:/home/centos/apache-tomcat-7.0.94/webapps"
                 }
            }
        }
    }
}
