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

        stage(' BUILD ') {
            steps {
            sh ' npm run build --prod'
            }
        }



        stage(' COPY ') {
            steps {
            sh ' cp -a /var/lib/jenkins/workspace/angularproject/dist/angularappproject/. /var/www/angular_project/html/'
            }
        }
     }
}