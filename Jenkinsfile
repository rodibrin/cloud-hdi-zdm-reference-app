@Library('piper-lib-os') _

node() {

  stage('prepare') {

    checkout scm

    setupCommonPipelineEnvironment script:this
  }

  def mtarBlue

  stage('build') {
    dir("cloud-hdi-zdm-ref-app.blue/mta-jee") {
      mtarBlue = mtaBuild script: this
    }
  }
  
  echo "deploy mtar=${mtaBlue}"
  
  stage('deploy') {
    cloudFoundryDeploy( script: this,
                        mtaPath: 'cloud-hdi-zdm-ref-app.blue/mta-jee/cloud-hdi-zdm-ref-app.mtar', 
                        mtaExtensionDescriptor:'config.mtaext'
    )
  }
}
