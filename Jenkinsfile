pipeline {
    agent {
        label 'built-in'
        customWorkspace '/mnt/MyWorkspace'
    }

    stages {
        stage('One') {
            steps {
                sh '''
                echo "Removing old containers (if any)"
                docker ps -aq | xargs -r docker rm -f

                echo "Removing volume if exists"
                docker volume rm V1 || true

                echo "Creating volume"
                docker volume create V1

                echo "Fixing workspace permissions"
                chmod -R 777 /mnt/MyWorkspace

                echo "Running Apache container"
                docker run -dit \
                  -p 80:80 \
                  -v /mnt/MyWorkspace:/usr/local/apache2/htdocs \
                  --name cont1 \
                  httpd
                '''
            }
        }
    }
}


