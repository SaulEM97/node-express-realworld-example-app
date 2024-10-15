pipeline {
    agent any
    environment{
        DATABASE_URL='postgresql://postgres:Assasinsegg97$%@localhost:5432/postgres'
        JWT_SECRET='8afc12c43d786ac377eedab5ccbb782a5ee66d6650fee067a3caa2b63b114174'
        NODE_ENV='production'
        npm_config_yes='true npx init'
    }
    stages {
        stage('Build') {
            steps {
                nodejs('NodeJS16.20.1'){
                    sh 'npm cache clean --force'
                    sh 'rm package-lock.json'
                    sh 'npm install'
                    sh 'nx migrate'
                    sh 'npm install'
                    sh 'nx migrate --run-migrations=migrations.json'
                    sh 'npm start'  
                }
            }
        }
    }  
}

