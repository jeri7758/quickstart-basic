pipeline {
    agent any

    stages {
        stage ('source code fetch') {
            steps {
            git branch: 'master', changelog: false, poll: false, url: 'git@github.com:jeri7758/quickstart-basic.git'
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
        stage ('Deploying app') {
            steps {
            sh '''
            rsync -rvz -e 'ssh -p 2232' ./ root@13.233.183.123:/var/www/html/laravel/
            ssh root@13.233.183.123 -p2232
            chown -R www-data. /var/www/html/laravel
            cd /var/www/html/laravel
            php artisan config:cache
            '''
            }
        }      
    }
}
