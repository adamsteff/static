pipeline{
    agent any
    stages{
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        },
        stage('Upload to AWS') {
            steps{
                withAWS(region:'ap-southeast-2',credentials:'aws-static') {
                    s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-jenkins-asteff')
                }
            }
        }
    }
}