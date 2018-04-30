node()
{
    stage "Checkout Code"
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/maheshkharwadkar/game-of-life.git']]])
    
    stage "build java project"
        sh 'cd /var/lib/jenkins/workspace/game-of-life-Pipeline'
        sh 'mvn clean install'
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        
     stage "Test"
                sh 'cd /var/lib/jenkins/workspace/game-of-life-Pipeline'
                sh 'mvn clean test'
                junit '**/target/surefire-reports/*.xml' 
}
