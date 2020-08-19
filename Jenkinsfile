@Library('piper-library-os') _

node() {

  stage('prepare') {

      checkout scm

      setupCommonPipelineEnvironment script:this

           checkChangeInDevelopment script: this,changeDocumentId:'8000001754'     
    
       }
 stage('build') {
      mtaBuild script: this
  }
   stage('CreateRepo') {
  gctsCreateRepository script: this
     host: 'http://hcluks4hana.hcldigilabs.com:8001',
  client: '000',
  abapCredentialsId: 'ABAPUserPasswordCredentialsId',
  repository: 'myrepo',
  remoteRepositoryURL: 'https://github.com/user/myrepo',
  role: 'SOURCE',
  vSID: 'ABC'
  }
  stage('neoDeploy') {
       neoDeploy script: this
  }
  stage('solmanTrCreate') {
      transportRequestCreate script:this, changeDocumentId:'8000001754',developmentSystemId: 'CD1~EXT_SRV',applicationId: 'HCP'
  }
   stage('solmanUpload') {
      transportRequestUploadFile  script:this, changeDocumentId:'8000001754',developmentSystemId: 'CD1~EXT_SRV',applicationId: 'HCP'
  }
}
