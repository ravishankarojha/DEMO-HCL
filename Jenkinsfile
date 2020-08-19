@Library('piper-library-os') _

node() {

  stage('prepare') {

      checkout scm

      setupCommonPipelineEnvironment script:this

           checkChangeInDevelopment script: this,changeDocumentId:'8000000309'     
    
       }
 stage('build') {
      mtaBuild script: this
  }
  
  stage('neoDeploy') {
       neoDeploy script: this
  }
  stage('solmanTrCreate') {
      transportRequestCreate script:this, changeDocumentId:'8000000309',developmentSystemId: 'CD1~EXT_SRV',applicationId: 'HCP'
  }
   stage('solmanUpload') {
      transportRequestUploadFile  script:this, changeDocumentId:'8000000309',developmentSystemId: 'CD1~EXT_SRV',applicationId: 'HCP'
  }
}
