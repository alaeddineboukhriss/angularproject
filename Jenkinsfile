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
        stage(' install node modules ') {
            sh "npm install"
     
        }

        stage(' build ') {
            sh "ng build --prod"
     
        }
     }
}