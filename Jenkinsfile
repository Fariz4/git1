pipeline{
    agent none
    stages{
        stage('build'){
            agent{
                label 'buildnode'
            }
            steps{
                deleteDir()
                sh'''
                git clone https://github.com/Fariz4/git1.git
                ls -la
                '''
                stash name:'webpage',
                includes:'git1/**'
            }
        }
        stage('deploy'){
            agent{
                label 'deploynode'
            }
            steps{
                deleteDir()
                unstash'webpage'
                sh'''
                rm -rf /var/www/html/*
                cp -r git1/* /var/www/html/
                ls -la /var/www/html/
                '''
            }
        }
    }
}
