pipeline {
    agent any
    tools {
        maven 'maven 3.8.6'
    }
    stages {
        stage ('git') {
            steps {
                git 'https://github.com/narendralucky333/-jenkins-maven-project.git'
            }
        }       
        stage('Build') {
            steps {
                sh 'mvn -f hello-app/pom.xml -B -DskipTests clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts....."
                    archiveArtifacts artifacts: '**/*.jar'
                }
            }
        }
        stage('Test') {
            steps {
                sh 'mvn -f hello-app/pom.xml test'
            }
            post {
                always {
                    junit 'hello-app/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
