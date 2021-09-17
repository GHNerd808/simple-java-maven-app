pipeline {
    agent any

    tools {
        maven 'jenkins_maven'
    }

    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }

        stage('package') {
          steps {
            sh 'mvn -B -DskipTests clean package'
          }
        }

        stage('test') {
          steps {
            sh 'mvn test'
          }
        }

        stage('deploy') {
          steps {
            sh '''
              echo "****************"
              echo "Deploying JAR"
              echo "****************"
              java -jar target/my-app-1.0-SNAPSHOT.jar
            '''

          }
        }
    }
}
