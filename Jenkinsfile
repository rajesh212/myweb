node{
    stage ('checkout'){
        git 'https://github.com/rajesh212/myweb'
    }
    stage('maven'){
        load 'maven'
    }
    stage('tomcat'){
          sshagent(['SLAVE']) {
        load 'tomcat'
    }
    }
}
