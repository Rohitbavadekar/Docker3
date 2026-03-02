pipeline {
    agent {
        label {
            label "built-in"
            customWorkspace "/mnt/MyWorkspace"
        }
    }

    stages {
        stage("One") {
            steps {
                sh "sudo docker ps -aq | xargs -r sudo docker rm -f"
                sh "sudo docker volume rm V1"
                sh "sudo chmod -R 777 /mnt/MyWorkspace"
                sh "sudo docker volume create V1"
                sh "sudo docker run -itdp 8080:80 -v /mnt/MyWorkspace:/usr/local/apache2/htdocs/ --name Cont3 httpd"
            }
        }
    }
}
