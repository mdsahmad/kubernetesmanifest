node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        bat 'git config user.email mdshahid.ahmad@outlook.com'
                        bat 'git config user.name mdsahmad'
                        //sh "git switch master"
                        bat 'cat deployment.yaml'
                        bat "sed -i \'s+raj80dockerid/test.*+raj80dockerid/test:${env.BUILD_NUMBER}+g\' deployment.yaml"
                        bat 'cat deployment.yaml'
                        bat 'git add .'
                        bat 'git commit -m "Done by Jenkins Job changemanifest"'
                        bat 'git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main'
      }
    }
  }
}
}
