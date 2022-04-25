pipeline {
    agent any

    stages {
        stage ('source code fetch') {
            git branch: 'master', changelog: false, poll: false, url: 'git@github.com:jeri7758/quickstart-basic.git'
        }
        
        stage ('Install dependencies') {
            sh 'composer install'
        }
        stage ('Database syn')  {
            sh 'php artisan migrate'
        }
        stage ('Serving app') {
            sh 'php artisan serve --host 10.160.0.2'
        }      
    }
}