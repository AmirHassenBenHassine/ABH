pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }
        stage('Send Email') {
            steps {
                emailext(
                    subject: "Nouveau Commit",
                    body: """
                        Un nouveau commit a été détecté dans le dépôt.
                        
                        Détails du commit :
                        
                        Message du commit : \${DEFAULT_LOG}
                        
                        Committer : \${GIT_COMMITTER_NAME} (\${GIT_COMMITTER_EMAIL})
                        """,
                    to: "amirbh07@gmail.com", // Remplacez par l'adresse e-mail de destination
                    mimeType: 'text/plain',
                    attachmentsPattern: 'README.txt' // Remplacez par le nom du fichier ou le modèle souhaité
                )
            }
        }
    }
}
