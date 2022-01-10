podTemplate(containers: [
    containerTemplate(
        name: 'helm', 
        image: 'alpine/helm:3.7.2', 
        command: 'sleep', 
        args: '30d'
        ),
  ]) {
    node(POD_LABEL) {
        stage('Helm project') {
            container('helm') {
                stage('Build a Helm project') {
                    sh '''
                    echo "Helm Building"
                    '''
                    sh 'helm version'
                }
            }
        }
    }
}