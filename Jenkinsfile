def server = Artifactory.newServer('http://18.207.229.179:8081/artifactory', 'admin', 'art123')

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'ant -f build.xml run'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                 /*def uploadSpec = """{
                  "files": [
                    {
                      "pattern": "classes/abc/*",
                      "target": "generic-local/"
                    }
                 ]
                }"""
                server.upload(uploadSpec)*/
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                mail body: 'project build successful for job named testpipeline-1',
                from: 'krk835900@gmail.com',
                subject: 'project build successful',
                to: 'krk835900@gmail.com'
            }
        }
    }
}


def downloadSpec = """{
 "files": [
  {
      "pattern": "classes/abc/*",
      "target": "generic-local/"
    }
 ]
}"""
