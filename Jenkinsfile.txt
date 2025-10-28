pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/yourname/ShoppingBill.git'
            }
        }
        stage('Build Java') {
            steps {
                bat 'javac ShoppingBill.java'
            }
        }
        stage('Run Java') {
            steps {
                bat 'java ShoppingBill'
            }
        }
        stage('Deploy HTML') {
            steps {
                bat 'mkdir output'
                bat 'copy index.html output\\index.html'
            }
        }
        stage('Notify Deployment') {
            steps {
                echo 'Deployment successful — Jenkins notification sent!'
            }
        }
    }
}
