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
                echo 'Testing..'
		sh 'mvn test'
            }
        }
        stage('deploy') {
            steps {
                echo 'Deploying....'
		sshagent(['pipelinep']) {
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkinspipeline_job/target/webapp-0.2.war ubuntu@54.174.103.155:/home/ubuntu/apache-tomcat-10.0.27/webapps"
		 }
            }
        }
    }
}
