pipeline {
  agent any
  stages {
    stage('Tool Check') {
      parallel {
        stage('Tool Check') {
          steps {
            sh '''git --version
java -version
terraform version'''
          }
        }

        stage('EmailBuild') {
          steps {
            emailext(subject: 'TF Build Starts', body: 'We are starting the TF Build', replyTo: 'rejcld@gmail.com', to: 'rejishs@gmail.com')
          }
        }

      }
    }

    stage('TF Init') {
      steps {
        sh '/usr/bin/terraform init'
      }
    }

    stage('TF Plan') {
      steps {
        sh '/usr/bin/terraform plan'
      }
    }

    stage('TF Apply') {
      steps {
        sh '/usr/bin/terraform apply -input=false -auto-approve'
      }
    }

    stage('Final') {
      steps {
        echo 'Completed'
      }
    }

  }
}