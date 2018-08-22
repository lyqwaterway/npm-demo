node {
    stage('Prepare') {
        sh 'jfrog rt c rt-server-1 --url=http://demo.jfrogchina.com/artifactory --apikey=AKCp2WXCWmSmLjLc5VKVYuSeumtarKV7TioZfboRAEwC1tqKAUvbniFJqp7xLfCyvJ7GxWuJZ'
        sh 'jfrog rt use rt-server-1'
    }
    stage('SCM') {
        git([url: 'https://gitlab.com/fuhui/npm-demo.git', branch: 'master', credentialsId: 'justin-gitlab2'])
    }
    stage('Build') {
        sh 'jfrog rt npm-install cai-npm-virtual --build-name=fuhui-npm-demo --build-number=100'
        sh 'jfrog rt bce fuhui-npm-demo 100'
    }
    stage('Publish') {
        sh 'jfrog rt npm-publish cai-npm-virtual --build-name=fuhui-npm-demo --build-number=100'
        sh 'jfrog rt bp fuhui-npm-demo 100'
    }
}