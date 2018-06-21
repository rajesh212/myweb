node{
    stage ('checkout'){
        git 'https://github.com/rajesh212/myweb'
    }
    stage('maven'){
        load 'maven'
    }
    stage('Tomcat Via ansible '){
          sshagent(['SLAVE']) {
        load 'tomcat_ansible'
    }
    }
}
