pipeline {
  agent any
  stages {
    stage('Delete Previous folders') {
      steps {
        sh '''ssh azureuser@20.106.158.162 "
 sudo rm -rf *
 sudo rm -rf /var/www/html/* "
'''
      }
    }

    stage('rsync') {
      steps {
        sh '''rsync -av /var/lib/jenkins/workspace/food azureuser@20.106.158.162:food
'''
      }
    }

    stage('Deployment in remote server') {
      steps {
        sh '''ssh azureuser@20.106.158.162 "
cd food/food
sudo cp -r . /var/www/html '''
      }
    }

  }
}
