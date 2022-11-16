pipeline {
    agent any

    tools {
        nodejs 'NODE_HOME'
    }
    
stages {
    stage('Getting project from Github') {
            steps {
                git branch : 'main' ,
                git branch: 'main', url: 'https://github.com/Snoussi22/front.git',
               
            }
        }
        stage('Install') {
            steps { 
                sh 'npm install'
            }
        }
        stage('Build') {
          steps { 
              sh 'npm run build'
              }
        }
        
        stage ('Build our image'){
            steps{
                sh 'docker build -t snoussi22/achat_front .'
            }
        }
        stage('Docker login')
        {
            steps {
                sh 'echo $dockerhub_PSW | docker login -u snoussi22 -p dckr_pat_TXLxayoJ-hAhuMiGu4Rutyp0tMo'
            }    
       
        }
      stage('Push') {

			steps {
				sh 'docker push snoussi22/achat_front'
			}
		}
    }
}
