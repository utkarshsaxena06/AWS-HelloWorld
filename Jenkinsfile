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
              sh '''whoami
                    cp -r ${WORKSPACE}/target/*.jar /opt/hello-world
                    cd /opt/hello-world
                    java -jar jb-hello-world-maven-0.1.0.jar
                 '''
            }
        }
    }
}
