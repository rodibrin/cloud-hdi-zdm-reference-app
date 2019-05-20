@Library('piper-lib-os') _

node() {

  stage('prepare') {

    checkout scm

    setupCommonPipelineEnvironment script:this
  }

  stage('build') {
    dir("cloud-hdi-zdm-ref-app.blue/mta-jee") {
      mtaBuild script: this
    }
    dir("cloud-hdi-zdm-ref-app.green/mta-jee") {
      mtaBuild script: this
    }
  }
}
