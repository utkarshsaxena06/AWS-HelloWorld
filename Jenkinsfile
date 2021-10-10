pipeline {
    agent { label 'master'}
    stages {
        stage('build') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
        }
        stage('deploy') {
            steps {
              sh 'cp -r ${WORKSPACE}/*.jar /opt/hello-world'
                 'cd /opt/hello-world'
                 'nohup java -Dserver.port=8888 -jar jb-hello-world-maven-0.1.0.jar &'
            }
        }
    }
}
