pipeline {
    agent any
    environment{
        DATABASE_URL='postgresql://postgres:Assasinsegg97$%@localhost:5432/postgres'
        JWT_SECRET='8afc12c43d786ac377eedab5ccbb782a5ee66d6650fee067a3caa2b63b114174'
    }
    stages {
        stage('Build') {
            steps {
                nodejs('NodeJS16.20.1'){
                    sh 'npm install'
                    sh 'npm audit fix --force'
                    sh 'npx prisma generate'
                    sh 'npx prisma migrate deploy'
                    sh 'npx nx init --interactive=false'
                    sh 'node dist/api/main.js'
                    sh 'npx prisma db seed'
                }
            }
        }
    }  
}

