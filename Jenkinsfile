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
            pipeline {
    agent {
        // define agent details
    }
    stages {
        stage('Deploy to staging') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'ssh&username', 
                                                   keyFileVariable: '', 
                                                   passphraseVariable: '', 
                                                   usernameVariable: '')]) {
    
                  }
                  // 
        
                sshPublisher(publishers: [sshPublisherDesc(configName: '
                                                          stage-server', 
                                                          transfers: [
                                                          sshTransfer(
                                                          cleanRemote: false, 
                                                          excludes: '', 
                                                          execCommand: '', 
                                                          execTimeout: 120000, 
                                                          flatten: false, 
                                                          makeEmptyDirs: false, 
                                                          noDefaultExcludes: false, 
                                                          patternSeparator: '[, ]+', 
                                                          remoteDirectory: '/var/www/html', 
                                                          remoteDirectorySDF: false, 
                                                          removePrefix: '', 
                       sourceFiles: '"/"')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)]) {
                  // 
                }
            }
        }
