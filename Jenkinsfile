pipeline{
    agent any
    stages{
        stage('SCM-CHECKOUT'){
            steps{
                git 'https://github.com/lakshmaiah212/hello-world.git'
            }
        }
        stage('code build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('deploy-artifact-ansible'){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'ansbile-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook -i /opt/docker/hosts /opt/docker/simple-devops.yml;', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//docker', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: 'webapp/target/webapp.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}
