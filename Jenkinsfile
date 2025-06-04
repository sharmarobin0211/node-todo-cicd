pipeline{
    agent any
    
    stages{
        stage("Code Clone"){
            steps{
                echo "Code Clone Stage"
                git url: "https://github.com/sharmarobin0211/node-todo-cicd.git", branch: "master"
            }
        }
        stage("Code Build"){
            steps{
                echo "Code Build Stage"
                sh " docker build -t todo-app:latest . "
                
            }
        }
        stage("Push To DockerHub"){
            steps{
                withCredentials([usernamePassword(
                    credentialsId:"dockerHubCreds",
                    usernameVariable:"dockerHubUser", 
                    passwordVariable:"dockerHubPass")]){
                sh 'echo $dockerHubPass | docker login -u $dockerHubUser --password-stdin'
                sh "docker image tag todo-app:latest ${env.dockerHubUser}/todo-app:latest"
                sh "docker push ${env.dockerHubUser}/todo-app:latest"
                }
            }
        }
        stage("deploy"){
            steps{
                sh "docker compose up "
            }
        }
    }
}
