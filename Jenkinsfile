pipeline {
    agent any
    environment {
        youtubePath = 'https://youtube.com'
        httpBinUrl = 'https://httpbin.org'
    }
    stages {
        stage('etape 1') {
            steps {
                echo 'Bonjour monde !'
                script {
                    def x = 1
                    echo "${x}"
                }
            }
        }
        stage('etape 2') {
            parallel {
                stage('etape 2.1') {
                    steps {
                        echo "${httpBinUrl} lien vers httpbin"
                    }
                }
                stage('etape 2.2') {
                    steps {
                        echo "${youtubePath} lien vers youtube"
                    }
                }
            }
        }
        stage('etape 3') {
            parallel {
                stage('etape 3.1') {
                    steps {
                        script {
                            try {
                                def response = httpRequest '${youtubePath}'
                            } catch (Exception e) {
                                error "Erreur : ${e.message}"
                            }
                        }
                    }
                }
                stage('etape 3.2') {
                    steps {
                        script {
                            try {
                                def response = httpRequest '${httpBinUrl}/get'
                            } catch (Exception e) {
                                error "Erreur : ${e.message}"
                            }
                        }
                    }
                }
            }
        }
    }
    post {
        success {
            echo "Le script s'est bien exécuté"
        }
        failure {
            echo "Le scrip ne s'est pas bien exécuté"
        }
        always {
            echo "Fin d'exécution"
        }
    }
}
