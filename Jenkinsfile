node {
    stage('git checkout') {
    checkout([$class: 'GitSCM',
    branches: [[name: '*/master']],
    doGenerateSubmoduleConfigurations: false,
    extensions: [], submoduleCfg: [],
    userRemoteConfigs: [[url: 'https://github.com/Akashs1218/jenkins']]])
    }
    
    stage ('app build') {
        sh 'mvn clean package'
    }
    
    stage ('Archive') {
        archiveArtifacts'target/Helloworldwebapp.war'
    }
    
    input 'Deploy to Prod server?'
    
    stage ('deploy') {
        sh 'cp target/Helloworldwebapp.war /opt/tomcat/webapps'
    }
    
    mail bcc: '',
    body: 'job finished', cc: '',
    from: '', replyTo: '',
    subject: 'jenkins job finished',
    to: 'akashs1218@gmail.com'

}    
