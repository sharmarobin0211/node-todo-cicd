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
      
    }
}
