pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    MULE_VERSION = '4.3.0'
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
	
	
  stage('Test') {
      steps {
          bat "mvn test"
      }
    }

     stage('Deploy Development') {
      environment {
        MULE_VERSION = '4.3.0'
        DEPLOY_CREDS_USR = "rajat.kumar1@apisero.com"
        DEPLOY_CREDS_PSW = "Nike@2015"
        APP_NAME= "helloworld_rk173346"
        ENVIRONMENT= "SANDBOX"
        BG = "Apisero Sandbox"
        WORKER = "Micro"
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