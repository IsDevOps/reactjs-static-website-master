pipeline{
    agent any

    stages{
        stage("Installing Dependencies"){
            steps{
                sh "npm install"
            }
        }
        stage("Run Build"){
            steps{
                sh 'export CI=false'
                sh "npm upgrade caniuse-lite browserslist"
                sh "npm run build"
            }
        }
        stage("Build Docker Image & Push"){
            steps{
                sh 'docker build -t oseghale1/tourApp:""$GIT_COMMIT"" .'
                sh 'docker push oseghale1/tourApp:""$GIT_COMMIT""'
            }  
        }
     }
    
}