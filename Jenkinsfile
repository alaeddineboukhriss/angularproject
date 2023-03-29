/*pipeline
{
    agent any
     stages {
      
        stage(' GIT ') {
            steps {
                echo 'Pulling...' + env.BRANCH_NAME
                checkout scm          
            }
        }
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
        }
     }
}*/
def getFirstWordFromGitBranch() {
    def gitBranch = sh(script: 'git rev-parse --abbrev-ref HEAD', returnStdout: true).trim()
    return gitBranch.tokenize('/')[0]
}

pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    def firstWord = getFirstWordFromGitBranch()
                    // Utilisez la variable firstWord dans les étapes suivantes
                }
            }
        }
        stage('Afficher la branche') {
            steps {
                echo "La branche active est : ${env.BRANCH_NAME}"
            }
        }
        
        // Autres étapes de la pipeline
        // ...
    }
}




