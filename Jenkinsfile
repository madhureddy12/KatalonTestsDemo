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
                katalonc -projectPath="/home/jenkins/agent/workspace/katalon/DemoProject_API_Feb2019.prj" -retry=0 -testSuitePath="Test Suites/TestSuite1" -executionProfile="default" -browserType="Web Service" -apiKey="322794a9-309d-42d4-a9b2-ff2a82308828" --config -proxy.auth.option=NO_PROXY -proxy.system.option=NO_PROXY -proxy.system.applyToDesiredCapabilities=true
               '''
        }
      }
    }
  }
}
