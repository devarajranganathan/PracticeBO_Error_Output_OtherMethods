pipeline {
  agent any
  stages {
    stage('RunVBS_A') {
      steps {
        bat(script: 'cd "C:\\Devaraj\\Test\\" & Wscript "a.vbs"', returnStatus: true, returnStdout: true)
      }
    }
    stage('RepeatSteps') {
      steps {
        retry(count: 2) {
          bat(script: 'Wscript "C:\\Devaraj\\Test\\b.vbs"', returnStatus: true, returnStdout: true)
        }
        
      }
    }
    stage('Git_in defined Workspace') {
      steps {
        ws(dir: 'C:\\Devaraj\\Test\\A\\') {
          git(url: 'https://github.com/devarajranganathan/PracticeMaven_JUnit.git', branch: 'master', changelog: true, credentialsId: 'devarajranganathan')
        }
        
        build 'Rename'
        bat(script: 'cd "C:\\Devaraj\\Test\\A\\" & mvn test', returnStatus: true, returnStdout: true)
      }
    }
    stage('ChangeDir') {
      steps {
        dir(path: 'C:\\Devaraj\\Test\\B') {
          bat(script: 'Wscript "C:\\Devaraj\\Test\\c.vbs"', returnStatus: true, returnStdout: true)
        }
        
      }
    }
    stage('WaitforInput') {
      steps {
        input 'What to do now?'
      }
    }
  }
}