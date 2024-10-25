pipeline {
    agent  any

    environment {
        fileName = 'file.txt'
        username = 'Achille'
        REPOSITORY = 'https://github.com/chillo-tech/landingpage.git'
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
                sh "echo 'File ${params.name}'"
                sh "echo 'Extension ${params.extension}'"
                sh "echo 'Content ${params.content}'"
                sh "printenv"
                git url: "${REPOSITORY}", branch: "${BRANCH}"
                sh "echo 'Content ${params.content}'"
            }
        }

        stage('build') {
            when {
                environment name: "file", value : "index"
            }
            steps {
                sh "echo 'Hello ${env.username}' > ${params.file}.${params.extension}"
               sh "echo ${params.content} > ${params.name}.${params.extension}"
            }
        }

        stage('Update commits') {
            steps {
                sh 'ls -al'
                sh '''
                    npm --version
                '''
                sh """
                    git config user.email ${env.EMAIL}
                    git config user.name ${env.USER_NAME}
                    git add .
                    git commit -am "Fichier ${params.name}.${params.extension}"
                """
            }
        }


        stage('check') {
            steps {
                sh 'ls -al'
            }
        }
    }
}