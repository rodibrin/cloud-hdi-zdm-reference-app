@Library('piper-lib-os') _

node() {

  stage('prepare') {

    checkout scm

    setupCommonPipelineEnvironment script:this
  }

  stage('build') {
    dir("cloud-hdi-zdm-ref-app.blue/mta-jee") {
      mtaBuild script: this, mtar: 'cloud-hdi-zdm-ref-app-blue-0.0.1.mtar'
    }
  }
  
  stage('deploy') {
  // cf bg-deploy ./cloud-hdi-zdm-ref-app.blue/mta-jee/cloud-hdi-zdm-ref-app-blue-0.0.1.mtar -e config.mtaext
    dir("cloud-hdi-zdm-ref-app.blue/mta-jee") {
      cloudFoundryDeploy( script: this, cloudFoundry: [mtaPath: 'cloud-hdi-zdm-ref-app-blue-0.0.1.mtar'] )
    }
  }
}
