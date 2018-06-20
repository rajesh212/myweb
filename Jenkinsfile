   node{
    stage('GIT CHECKOUT'){
         load 'git'
    }
    stage('MAVEN'){
        load 'maven'
    }
    stage('TOMCAT'){
         def tomcat_location = 'ec2-user@172.31.91.92:/opt/tomcat/webapps'
         def shutdown = '/opt/tomcat/bin/shutdown.sh'
         def startup = '/opt/tomcat/bin/startup.sh'
        sshagent(['SLAVE']) {
    sh "scp -o StrictHostKeyChecking=no target/myweb.war ${tomcat_location}"
    sh "ssh ec2-user@172.31.91.92 ${shutdown}"
    sh "ssh ec2-user@172.31.91.92 ${startup}"
    }
    }
}
