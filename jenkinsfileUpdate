node {
  def app
  stage('Clone repository') {
    checkout scm
    }
  
  stage('Update GIT') {
    script {
      catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
        withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]){
          //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
         sh "git config user.email 30shiwamyasinha@gmail.com"
         sh "git config user.name Shivamya30"
         //sh "git switch master"
         sh "cat deployment.yaml"
         sh "sed -i 's+public.ecr.aws/e4j0o0u9/ecr-demoing.*+public.ecr.aws/e4j0o0u9/ecr-demoing:${env.BUILD_ID}+g' deployment.yaml"
         sh "cat deployment.yaml"
         sh "git add ."
         sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_ID}'"
         sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernete.git HEAD:master"
       }
     }
   }
 }
}
