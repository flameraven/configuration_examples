node('masterLin'){
    
    wrap([$class: 'TimestamperBuildWrapper']){
        wrap([$class: 'AnsiColorBuildWrapper']){
            wrap([$class: 'BuildUser']) {
                starter_email = env.BUILD_USER_EMAIL 
                starter_name = env.BUILD_USER
                starter_name_id = env.BUILD_USER_ID
            }
            currentBuild.result = 'SUCCESS'       

            deleteDir()

            stage('Clone git'){
                git branch: 'master',
                url: 'https://github.com/flameraven/test_pipeline.git'
            }

            stage('Build docker image'){
                app = docker.build('192.168.57.103:8083/test_images')
            }

            stage('Test image') {
                app.inside {
                    sh 'echo "Tests passed"'
                }
            }

            stage('Push image'){
                docker.withRegistry('https://192.168.57.103:8083', 'docker_registry') {
                app.push("${env.BUILD_NUMBER}")
                app.push("latest")                

            }
            
//            sh "echo 'Hello World'"
        }
    }
}