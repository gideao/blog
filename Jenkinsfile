pipeline {
  agent { dockerfile true }
  
  stages {
    stage('Build') {
      steps {
        sh 'jekyll build'
      }
    }

    stage('Deploy') {
      environment { 
        AWS_ACCESS_KEY_ID = credentials('aws-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-access-key')
        AWS_DEFAULT_REGION = 'sa-east-1'
      }

      steps {
        sh 'aws s3 sync _site s3://www.gideao.co --delete'
      }
    }
  }
}
