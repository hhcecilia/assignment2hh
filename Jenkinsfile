pipeline {
    agent any

    environment {
        NETLIFY_SITE_ID = '4b6ceb0e-594a-406c-8396-48b8435506eb'
        NETLIFY_AUTH_TOKEN = credentials('netlify-token')
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'CI=true npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'npm install -g netlify-cli'
                sh 'netlify deploy --prod --dir=build --site=$NETLIFY_SITE_ID --auth=$NETLIFY_AUTH_TOKEN'
            }
        }
    }
}
