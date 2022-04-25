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
        stage ('Deploying app') {
            sh 'rsync -rvz -e 'ssh -p 2232' ./* root@52.66.209.9:/var/www/html/laravel/'
        }      
    }
}