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
  
  stage('deploy') {
    cloudFoundryDeploy( script: this,
                        mtaPath: mtarBlue, 
                        mtaExtensionDescriptor:'config.mtaext'
    )
  }
}
