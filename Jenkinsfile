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
		sshagent(['admin'])
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkins-cicd/target/webapp-0.2.war centos@18.208.206.41:/home/centos/apache-tomcat-7.0.94/webapps"
		 }
            }
        }
    }
}
