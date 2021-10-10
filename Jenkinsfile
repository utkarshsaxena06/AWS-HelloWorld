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
                    cp -r ${WORKSPACE}/target/*.jar /home/ec2-user/hello-world
                    cd /home/ec2-user/hello-world
                    nohup java -Dserver.port=8888 -jar jb-hello-world-maven-0.1.0.jar &
                 '''
            }
        }
    }
}
