pipeline {
    agent any
    stages {
        stage('WSO2')   {
             steps {
                withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId:'wso2', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
                  sh 'apictl login dev -u $USERNAME -p $PASSWORD -k'
                }
                sh('cp -r ../WSOAPIM-POC ../${BUILD_NUMBER}')
                sh('pwd && ls && cd .. && pwd && ls')
                sh('apictl import api --file ../${BUILD_NUMBER} --environment dev')
                sh('rm -r ../${BUILD_NUMBER} ')
            }
        }
        stage('delete workspace') {
            steps {
               cleanWs cleanWhenAborted: false, cleanWhenFailure: false, cleanWhenNotBuilt: false, cleanWhenUnstable: false, notFailBuild: true
            }
        }
    }
    post {
        always {
        //cleanup workspace.
          cleanWs()
        }
    }
}
