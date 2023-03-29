pipeline
{
    agent any
     stages {
      
        stage(' GIT ') {
            steps {
                echo 'Pulliing ...';
                git branch: 'master', url: 'https://github.com/alaeddineboukhriss/angularproject.git'          
            }
     
        }
       stage('Extract branch name') {
            steps {
                script {
                    def extractBranchNameFromConsoleOutput() {
                        def consoleOutput = currentBuild.rawBuild.getLog(1000) // Récupérer les 1000 premières lignes du log de la build
                        def branchName = consoleOutput =~ /origin\/(\S+)/ // Utiliser une expression régulière pour extraire le nom de la branche
                        if (branchName) {
                            return branchName[0][1] // Retourner le premier groupe de capture
                        } else {
                            return ""
                        }
                    }

                    def branchName = extractBranchNameFromConsoleOutput()
                    println "Le nom de la branche est ${branchName}"
                }
            }
      /* stage(' install node modules ') {
            steps {
            sh ' npm install' 
            
            }
        }


        stage(' BUILD ') {
            steps {
            sh ' npm run build --prod'
            }
        } 

        stage(' BUILD ') {
            steps {
                script {
                    sh ' ansible-playbook ansible/build.yml -i ansible/inventory/host.yml '
                 }
            }
        }

        stage(' DOCKER ') {
            steps {
                script {
                    sh ' ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml '
                 }
            }
        }


        stage(' DOCKER REGISTRY') {
            steps {
                withDockerRegistry([credentialsId: "docker-hubb", url: ""]) {
                script {
                    sh ' ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml '
                 }
                 }
            }
        }

        stage(' COPY ') {
            steps {
            sh 'mv /var/lib/jenkins/workspace/angularproject/dist/angularappproject/. /var/www/angular_project/html/'
            }
        }  */
     }
}
