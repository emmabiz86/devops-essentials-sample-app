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
            when {
                branch 'master'
            }
                   steps {
                    withCredentials([sshUserPrivateKey(credentialsId: 'ssh&username', keyFileVariable:    'stage-server', passphraseVariable: '', usernameVariable: 'ec2-user')]) {
                  // some block
              sshPublisher(
                 publishers: 
                          [sshPublisherDesc(
                               configName: 'stage-server', transfers: 
                         [sshTransfer(
                              cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000,     flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/www/html', 
                                  remoteDirectorySDF: false, 
                                     removePrefix: '',
                                           sourceFiles: '"/"')], 
                                               usePromotionTimestamp: false, 
                                                   useWorkspaceInPromotion: false, 
                                                               verbose: false)])

                 }
               stage('DeployToProd') {
            when {
                branch 'master'
            }
            steps {
                input 'Does the staging environment look OK?'
                milestone(1)
               withCredentials([
                   sshUserPrivateKey(
                      credentialsId: 'ssh&username', keyFileVariable: 'deployment', 
                      passphraseVariable: '', usernameVariable: 'ec2-user')]) {
                      // some block
                      }
             sshPublisher(
                publishers: [
                   sshPublisherDesc(
                      configName: 'deployment',
                      transfers: [
                            sshTransfer(
                              cleanRemote: 
                                 false, excludes: '', 
                                          execCommand: '', 
                                           execTimeout: 120000, 
                                            flatten: false, 
                                             makeEmptyDirs: false, 
                                              noDefaultExcludes: false, 
                                               patternSeparator: '[, ]+', 
                                                remoteDirectory: '/var/www/html', 
                                                 remoteDirectorySDF: false, 
                                                  removePrefix: '', 
                                            sourceFiles: '"/"')], 
                                                  usePromotionTimestamp: false, 
                                                     useWorkspaceInPromotion: false, verbose: false)])

           }
