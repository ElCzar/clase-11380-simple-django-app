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
                script{
                    withPythonEnv('python3') {
                        sh 'pip install -r requirements.txt'
                    }
                }
              }
          }

        stage('test') {
            steps {
                script{
                    withPythonEnv('python3') {
                        sh 'pylint --ignore-paths=env ./cool_counters/*'
                    }
                }
            }
        }

        stage('deploy') {
            steps {
                script{
                    withPythonEnv('python3') {
                        sh 'python3 ./cool_counters/manage.py migrate'
                        sh 'python3 ./cool_counters/manage.py runserver'
                    }
                }
            }
        }
    }
}
