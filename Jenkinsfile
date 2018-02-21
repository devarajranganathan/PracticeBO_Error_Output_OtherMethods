pipeline {
  agent any
  stages {
    stage('RepeatSteps') {
      steps {
        retry(count: 3) {
          bat(script: 'Wscript "C:\\Devaraj\\Test\\a.vbs"', returnStatus: true, returnStdout: true)
        }
        
      }
    }
    stage('WorkspaceAllocation') {
      steps {
        ws(dir: 'C:\\Devaraj\\Test\\A\\') {
          build 'MultiJob_Jobs/B'
        }
        
      }
    }
  }
}