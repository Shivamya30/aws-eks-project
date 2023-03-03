pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        sh 'printenv'
        sh 'docker build -t webapp .'
      }
    }
    stage ('Publish ECR') {
      steps {
        withEnv (["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_-KEY_ID}", "AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}", "AWS_DEFAULT_REGION=$(env.AWS_DEFAULT_REGION}"]) {
          sh 'docker login -u AWS -p $(aws ecr get-login-password --region us-east-1) 117892039954.dkr.ecr.us-east-1.amazonaws.com'
          sh 'docker build -t webapp .'
          sh 'docker tag webapp:""$BUILD_ID""'
          sh 'docker push 117892039954.dkr.ecr.us-east-1.amazonaws.com/webapp:""$BUILD_ID""'
        }
      }
    }
  }
}         
