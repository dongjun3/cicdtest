pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/dongjun3/cicdtest', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t kdj5854/testweb:newnewmain .
        sudo docker push kdj5854/testweb:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
	sudo kubectl set image deployment deploy-main ctn-main=kdj5854/testweb:newnewmain
        '''
      }
    }
  }
}
