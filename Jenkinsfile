pipeline {
    agent any
    
    stages {
        stage('test1'){
            steps {
                echo "HELLO ALL1"
            }
        }
        
        stage('test2'){
            input {
                message "What is your name?"
                ok "Next"
                parameters {
                    string(name: 'NAME', defaultValue: 'GILDONG', description: 'type your name')
                }
            }
            
            steps {
                echo "HELLO ${NAME}"
            }
        }
        stage('test3'){
            input {
                message "Docker image tag name"
                ok "finished"
                parameters {
                    string(name: 'TAG', defaultValue: 'none', description: 'type docker image tag')
                }
            }
            steps {
                sh '''
                sudo rm -rf /var/lib/jenkins/workspace/testcicd/cicdtest
                git clone https://github.com/dongjun3/cicdtest
                cd cicdtest
                sudo docker build -t kdj5854/testweb:${TAG} .
                sudo docker push kdj5854/testweb:${TAG}
                '''
            }
            
        }
        
    }
    post {
        always {
            echo "작업완료 - 성공실패여부 모름"
            }
    }
}





