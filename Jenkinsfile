pipeline {
    agent any

    stages {
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
