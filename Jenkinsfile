// Jenkinsfile
        @Library('ma-lib-partagee') _ // Indique d'utiliser la bibliothèque 'ma-lib-partagee'
                                    // Le underscore (_) est important pour importer les vars et src

        pipeline {
            agent any

            stages {
                stage('Utiliser MonUtilitaire') {
                    steps {
                        script {
                            org.exemple.utils.MonUtilitaire.saluer(this, "Jenkins User")
                            def messageSucces = org.exemple.utils.MonUtilitaire.genererMessage("succes")
                            echo messageSucces
                        }
                    }
                }

                stage('Utiliser autreFonction') {
                    steps {
                        script {
                            def resultat = autreFonction("Ceci est un test de fonction globale.")
                            echo "Résultat de autreFonction : ${resultat}"
                        }
                    }
                }

                stage('Appeler monEtapePersonnalisee') {
                    steps {
                        monEtapePersonnalisee {
                            echo "Ceci est le contenu du bloc passé à monEtapePersonnalisee."
                            echo "On peut même appeler une fonction de la Shared Library ici :"
                            org.exemple.utils.MonUtilitaire.saluer(this, "De l'interieur de l'etape personnalisee")
                        }
                    }
                }
            }

            post {
                always {
                    echo "Pipeline terminé."
                }
            }
        }