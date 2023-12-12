
pipeline{
    agent any
    environment{
        staging_server="54.224.245.5"
    }
    stages{
        stage('Deploy to Remote'){
            steps{
                sh '''
                    for fileName in `find ${WORKSPACE} -type f -mmin -10 | grep -v ".git" | grep -v "Jenkinsfile"`
                    do
                        fil=$(echo ${fileName} | sed 's/'"${JOB_NAME}"'/ /' | awk {'print $2'})
                      
scp -o StrictHostKeyChecking=no -r -i ${JENKINS_HOME}/.ssh/id_rsa ${WORKSPACE}/index.php root@${staging_server}:/var/www/html/index.php

                    done
                '''
            }
        }
    }
}
