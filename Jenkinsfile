node {
   def commit_id
   stage('Preparation') {
     checkout scm
     sh "git rev-parse --short HEAD > .git/commit-id"
     commit_id = readFile('.git/commit-id').trim()
   }
   stage('docker build') {
     docker.image('myapp').withRun {c ->
       sh 'docker kill myapp  > /dev/null 2>&1'
       sh 'docker rm myapp  > /dev/null 2>&1'
       sh 'docker-compose up -d'
    }
    stage('Testing Application') {
     def response = sh(script: 'curl http://139.162.171.242:8000/', returnStdout: true)
     echo '=========================Response===================' + response

     }
   }
 }

