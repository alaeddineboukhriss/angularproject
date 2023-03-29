/*pipeline
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
        }
     }
}*/
pipeline {
    agent any

    stages {
        stage('Extract branch name') {
            steps {
                script {
                   def extractBranchNameFromConsoleOutput = {
                   def build = currentBuild.rawBuild
                   def listener = currentBuild.listener
                   def branchName = build.environment.get('BRANCH_NAME')
                   if (branchName == null) {
                       branchName = build.logFile.text =~ 'Checking out ([^ ]+) ' ?: 'unknown'
                       if (branchName != 'unknown') {
                           branchName = branchName[0][1]
                       }
                   }
                   return branchName
                   }
                }
            }
        }
    }
}

