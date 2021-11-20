pipeline {
  agent any
  stages {
    stage('Git SCM ') {
      steps {
        git(url: 'https://github.com/pavansw/simpleMavenJunit.git', branch: 'master', changelog: true, poll: true)
        sleep 3
      }
    }

    stage('CompileCode') {
      steps {
        sh 'mvn compile'
      }
    }

    stage('testing') {
      parallel {
        stage('testing') {
          steps {
            sh 'mvn test'
          }
        }

        stage('testing2') {
          steps {
            echo 'This is testing 2'
          }
        }

      }
    }

    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }

    stage('Execute') {
      steps {
        echo 'Run Jar file here'
      }
    }

  }
}