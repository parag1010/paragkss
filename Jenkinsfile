pipeline {

agent any
triggers { cron('*/5 * * * *') }

   stages {

stage ('Git Checkout') {
steps	{
script {
try {
timeout(time: 20, unit: 'SECONDS') {

checkout([$class: 'GitSCM', branches: [[name: '*/']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '10e71e557ac1a09b7789c451c666d264b38b3c33', url: 'https://github.com/Amanjain1612/intellimeet-CICD.git']]])

 	  }

}

catch(err) {
               err.printStackTrace()
                                               }
               sh 'echo Proceeding'
              }
           }
}
stage("Run Tests") {
       	agent { docker "maven:3.5-jdk-8" }
           	steps {
sh 'mvn package'

withEnv(["PATH+MAVEN=${tool 'maven3'}/bin"]) {
sh "mvn test"
}
}

}


}
}
