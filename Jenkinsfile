pipeline {
    agent  any

    environment {
        fileName = 'file.txt'
        username = 'Achille'
        GIT_CREDENTIALS = credentials('github-chillotech-pat')
        GIT_CREDENTIALS_ID = 'github-pat'
        REPOSITORY = 'https://github.com/chillo-tech/jenkins-pipelines.git'
        BRANCH = "main"
        EMAIL =  "achille.mbougueng@chillo.tech"
        USER_NAME = "chillo-tech"
    }

    parameters {
        string(name: "file", defaultValue: "user-card")
        string(name: "name", defaultValue: "user-card")
        text(name: "content")
        choice(name: "extension", choices: ['txt', 'docx'])
    }

    stages {
        stage ('Initialtisation') {
            steps {
                
                checkout (
                    $class: 'GitSCM',
                    branches: [[name: env.BRANCH]],
                    userRemoteConfigs: [[
                        credentialsId: env.GIT_CREDENTIALS_ID,
                        url: env.REPOSITORY
                    ]]
                )

                sh "echo 'File ${params.name}'"
                sh "echo 'Extension ${params.extension}'"
                sh "echo 'Content ${params.content}'"
                sh "printenv"
                git url: "${REPOSITORY}", branch: "${BRANCH}"
                sh "echo 'Content ${params.content}'"
            }
        }

        stage('build') {
            steps {
                sh "echo 'Hello ${env.username}' > ${params.file}.${params.extension}"
                sh "echo ${params.content} >> ${params.name}.${params.extension}"
            }
        }

        stage('Update commits') {
            steps {
                sh 'ls -al'
                sh """
                    git config user.email ${env.EMAIL}
                    git config user.name ${env.USER_NAME}
                    git add .
                    git commit -am "Fichier ${params.name}.${params.extension}" || true
                """
            }
        }


        stage('update remote repository') {
            steps {
                withCredentials([gitUsernamePassword(credentialsId: 'github-chillotech-pat', gitToolName: 'Default')]) {
                    sh 'git push --set-upstream origin main'
                }
            }
        }
    }
}
