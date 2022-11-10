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

/*
        stage(' BUILD ') {
            steps {
            sh ' npm run build --prod'
            }
        } */

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


        /*stage(' COPY ') {
            steps {
            sh 'mv /var/lib/jenkins/workspace/angularproject/dist/angularappproject/. /var/www/angular_project/html/'
            }
        }*/
     }
}