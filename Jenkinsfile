pipeline {
    agent any
    stages {
        stage('WSO2')   {
             steps {
               // sh('apictl add env dev --apim https://api-portal-dev.yabie.com:443')
//                 sh('apictl init XYZ --oas https://apim.docs.wso2.com/en/4.0.0/assets/attachments/get_started/petstore.json')
//                 sh('sed -i -e "s/name: SwaggerPetstore/name: XYZ/" XYZ/api.yaml')
//                 sh('sed -i -e "s/name: SwaggerPetstore/name: XYZ/" XYZ/api_meta.yaml')
//                 sh('sed -i -e "s+context: /SwaggerPetstore+context: /XYZ+" XYZ/api.yaml')
//                 sh('sed -i -e "s/lifeCycleStatus: CREATED/lifeCycleStatus: PUBLISHED/" XYZ/api.yaml')
//                 sh('sed -i -e "s/version: 1.0.0/version: 2.1.0/" XYZ/api.yaml')
//                 sh('sed -i -e "s/version: 1.0.0/version: 2.1.0/" XYZ/api_meta.yaml')
//                 sh('sed -i -e "s+url: http://localhost:8080+url: https://petstore.swagger.io/v2+" XYZ/api.yaml')
//                 sh('sed -i -e "s+url: http://localhost:8081+url: https://petstore.swagger.io/v2+" XYZ/api.yaml')
//                 sh('sed -i -e "s+read:pets: read your pets+read:pets: read your petss+" XYZ/Definitions/swagger.yaml')
//                 sh('sed -i -e "s+write:pets: modify pets in your account+write:pets: modify pets in your accountt+" XYZ/Definitions/swagger.yaml')
                sh('apictl login dev -u jenkins-ci -p Jenkinscicd -k')
                sh('pwd && ls && cd .. && pwd && ls')
                 sh('apictl import api --file ./WSOAPIM-POC --environment dev')
                //sh('apictl import api --file ../WSOAPIM-POC --environment dev')
                 //sh('apictl import api --file ../WSOAPIM-POC --environment dev --preserve-provider=false --update=true --rotate-revision --verbose ')
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
