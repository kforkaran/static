pipeline {
  agent any 
    stages {
      stage('Lint HTML') {
        steps {
          sh 'tidy -q -e *.html'
        }
      }
      stage('Upload to AWS') {
        steps {
          retry(3) {
            withAWS(region:'ap-south-1', credentials:'aws-static'){
            s3Upload(file:'index.html', bucket:'jenkins-bucket-1', path:'')
          }
        }
      }
    }
  }
}