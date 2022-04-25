pipeline {
    agent any

    stages {
        stage('source code fetch') {
            steps{
            git branch: 'develop', changelog: false, poll: false, url: 'git@github.com:jeri7758/quickstart-basic.git'
            }
        }
        stage ('Install dependencies') {
            steps {
            sh 'composer install'
            }
        }
        stage ('Database syn')  {
            steps {
            sh 'php artisan migrate'
            }
        }
        stage ('Serving app') {
            steps {
            sh 'php artisan serve --host 10.160.0.2'
            }
        }      
    }
}
