pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
		sh '/usr/share/maven/bin/mvn clean package'
'
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
		sshagent(['Deploy']) {
		sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkins-cicd/target/webapp-0.2.war centos@18.208.206.41:/home/centos/apache-tomcat-7.0.94-M1/webapps"
		 }
            }
        }
    }
}
