pipeline {
    agent { label 'master'}
    tools { 
        maven 'MVN_HOME'
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
        }
        stage('deploy') {
            steps {
              sh '''sudo cp -r ${WORKSPACE}/target/*.jar /opt/hello-world
                 sudo cd /opt/hello-world
                 sudo nohup java -Dserver.port=8888 -jar jb-hello-world-maven-0.1.0.jar &
                 '''
            }
        }
    }
}
