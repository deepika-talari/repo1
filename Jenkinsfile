pipeline {

  agent {
      label 'deepika-localhost'
  }
  parameters {
    string(name: 'x', description: 'enter x')
    string(name: 'y', description: 'enter y')

  }
//   environment {
//       JENKINS = credentials('jenkins-token')
//   }
triggers {
        cron('0 15 * * *')
    }

  options {
    timeout(time: 15, unit: 'MINUTES')
  }

  stages {
    stage('Running python script - sum of nos') {
      steps {
        // withCredentials([
        //   usernamePassword(credentialsId: 'mvnmgr-github-readonly', passwordVariable: 'GITHUBPIE_PSW', usernameVariable: 'GITHUBPIE_USR')
        //   ])
              sh 'python3 sum.py '+"${params.x}" + ' '+"${params.y}" + ''
            
      }
    }
  }
  post {
    always {
      emailext body: 'Running python script - hello world', to: 'talarideepika48@gmail.com',
      recipientProviders: [[$class: 'CulpritsRecipientProvider'], [$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: "Hello world Report: '${env.JOB_NAME} ${env.BUILD_URL} '"
    //   archiveArtifacts artifacts: '*.csv'
      }
      cleanup {
        cleanWs()
      }
    }
  }
