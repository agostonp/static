pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'eu-central-1', credentials:'aws-static') {
                      sh 'echo "Uploading content to AWS S3 bucket arn:aws:s3:::ago-jenkins-pipeline"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'ago-jenkins-pipeline')
                  }
              }
         }


     }
}
