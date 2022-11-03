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
            steps {
            sh ' npm install' 
            
            }
        }

        stage(' build ') {
            steps {
            sh ' ng build --prod'
            }
        }
     }
}