pipeline {
  agent any
  stages {
    stage('RepeatSteps') {
      steps {
        retry(count: 3) {
          node(label: 'Priyanka') {
            bat(script: 'Wscript "C:\\Devaraj\\Test\\a.vbs"', returnStatus: true, returnStdout: true)
          }
          
        }
        
      }
    }
    stage('WorkspaceAllocation') {
      steps {
        node(label: 'Priyanka') {
          ws(dir: 'C:\\Devaraj\\Test\\A') {
            build 'MultiJob_Jobs/A'
          }
          
          ws(dir: 'C:\\Devaraj\\Test\\B') {
            build 'MultiJob_Jobs/B'
          }
          
        }
        
      }
    }
  }
}