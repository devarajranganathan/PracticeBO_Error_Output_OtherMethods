pipeline {
  agent any
  stages {
    stage('WorkspaceAllocation') {
      steps {
        ws(dir: 'C:\\Devaraj\\Test\\A') {
          bat(script: 'Wscript "b.vbs"', returnStatus: true, returnStdout: true)
        }
        
      }
    }
    stage('RunVBS_A') {
      steps {
        bat(script: 'Wscript "C:\\Devaraj\\Test\\a.vbs"', returnStatus: true, returnStdout: true)
      }
    }
    stage('RepeatSteps') {
      steps {
        retry(count: 2) {
          bat(script: 'Wscript "C:\\Devaraj\\Test\\b.vbs"', returnStatus: true, returnStdout: true)
        }
        
      }
    }
  }
}