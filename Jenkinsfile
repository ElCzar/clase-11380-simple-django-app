pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'source .venv/bin/activate'
              }
          }

        stage('test') {
            steps {
                sh 'pylint --ignore-path=./.venv ./'
            }
        }

        stage('deploy') {
            steps {
                sh 'python ./cool_counters/manage.py migrate'
                sh 'python ./cool_counters/manage.py runserver'

            }
        }
    }
}
