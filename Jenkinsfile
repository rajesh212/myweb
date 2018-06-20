node{
    stage('SCM CHECKOUT'){
        def java = 'https://github.com/javahometech/my-app'
        git branch:'master',url: "${java}"
    }
    def mhome = tool name: 'maven', type: 'maven'
    stage('MAVEN'){
        sh "${mhome}/bin/mvn clean package"
        sh 'mv target/myweb*.war target/myweb.war'
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
