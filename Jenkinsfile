pipeline {
    agent { label 'master'}
    tools { 
        maven 'MVN_HOME'
    }
    options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
    stages {
        stage('build') {
            steps {
                sh 'mvn -f pom.xml clean package -Dmaven.test.skip=true'
            }
        }
        stage('deploy') {
            steps {
              sh '''cp -r ${WORKSPACE}/target/*.jar /opt/hello-world
                    cd /opt/hello-world
                    #sudo systemctl start jar.service
                    #contains the java startup command
                    ./start.sh
                    #java -jar java-webapp-1.0.jar >/dev/null 2>&1
                 '''
            }
        }
    }
}
