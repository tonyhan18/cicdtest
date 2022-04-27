pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/tonyhan18/cicdtest.git', branch: 'main'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t tonyhan18/testshop:newnewmain .
        sudo docker push tonyhan18/testshop:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
	sudo kauth
	sudo kubectl set image deployment deploy-main ctn-main=tonyhan18/testshop:newnewmain
        '''
      }
    }
  }
}
