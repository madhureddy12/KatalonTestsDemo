pipeline {
  agent {
    kubernetes {
      //cloud 'kubernetes'
      yaml """
kind: Pod
metadata:
  name: kaniko
spec:
  containers:
  - name: katalon
    image: katalonstudio/katalon
    imagePullPolicy: Always
    command:
    - cat
    tty: true
"""
    }
  }
  stages {
    stage('Build') {
      steps {
        container('katalon') {
            sh '''
               pwd
               ls
               katalonc -retry=0 -testSuitePath="Test Suites/TestSuite1" -executionProfile="default" -browserType="Web Service" -apiKey="3722ae70-b9ee-4d81-aa08-d329d953c40e" --config -proxy.auth.option=NO_PROXY -proxy.system.option=NO_PROXY -proxy.system.applyToDesiredCapabilities=true
               '''
        }
      }
    }
  }
}
