pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: '192.168.2.156', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '192.168.2.184', description: 'Production Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
