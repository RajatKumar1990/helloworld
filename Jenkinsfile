pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    MULE_VERSION = '4.1.4'
    DEPLOY_CREDS_USR = "rajat.kumar1@apisero.com"
    DEPLOY_CREDS_PSW = "Nike@2015"
    APP_NAME= "helloworld_rk173346"
    ENVIRONMENT= "SANDBOX"
    BG = "Apisero Sandbox"
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'helloworld-rk173346'
      }
      steps {
            bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
  }

  tools {
    maven 'Maven3_6_3'
  }
}