podTemplate(containers: [
    containerTemplate(
        name: 'helm', 
        image: 'dtzar/helm-kubectl:3.7.2', 
        command: 'sleep', 
        args: '30d'
        ),
  ]) {
    node(POD_LABEL) {
        container('helm') {
            stage('Git Clone') {
                git 'https://github.com/susguzman/hello-world-helm.git'
                
            }
            stage('Linting') {
                sh 'helm lint'
            }
            stage('Testing') {
                sh 'echo "TODO ..."'
            }
            stage('Packaging') {
                sh 'helm package . -d build/'
            }
            stage('Publishing') {
                withCredentials([string(credentialsId: 'art_repo', variable: 'repo'), usernameColonPassword(credentialsId: 'art_creds', variable: 'creds')]) {
                    sh 'curl -u "$creds" -T build/hello-world-0.1.0.tgz "$repo"'
                }
            }
        }
    }
}