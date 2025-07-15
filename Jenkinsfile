pipeline {
    agent any
    environment {
        variable = "https://youtube.com"
    }
    stages {
        stage("etape 1") {
            steps {
                echo "Bonjour monde !"
                script {
                    def x = 1
                    echo "${x}"
                }
            }
        }
        stage("etape 2") {
            steps {
                echo "${variable} lien vers youtube"
            }
        }
        stage("etape 3") {
            steps {
                script {
                    try {
                        def response = httpRequest 'https://httpbin.org/get'
                    } catch (Exception e) {
                        error "Erreur : ${e.message}"
                    }
                }
            }
        }
    }
    post {
        success {
            echo "Le script s'est bien exécuter"
        }
        failure {
            echo "Le scrip ne s'est pas bien exécuter"
        }
        always {
            echo "Fin d'exécution"
        }
    }
}
