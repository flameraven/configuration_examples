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

            sh "echo 'Hello World'"
        }
    }
}