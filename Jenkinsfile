pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build'
                archiveArtifacts artifacts: 'src/index.html'
            }
        }
            stage('DeployToStage') {
  steps {
         withCredentials([sshUserPrivateKey(credentialsId: 'ssh&username', keyFileVariable: 'staging-server', passphraseVariable: '', usernameVariable:          '')]) {
         sshPublisher(publishers: [sshPublisherDesc(configName: 'stage-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '',          execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/www/html',          remoteDirectorySDF: false, removePrefix: '', sourceFiles: '"/"')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    // some block
}
    // One or more steps need to be included within the steps block.
  }

  agent any
}
