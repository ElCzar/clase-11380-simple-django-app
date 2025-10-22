pipeline {
    agent any
    stages {
        stage('pull') {
            steps {
                git branch: "main",
                    url: 'https://github.com/ElCzar/clase-11380-simple-django-app.git'
              }
          }
        
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
