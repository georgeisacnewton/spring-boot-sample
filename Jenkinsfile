node {
    stage('Checkout') {
        git 'https://github.com/bertjan/spring-boot-sample'
    }

     stage('Build') {
        sh 'mvn -B -V -U -e clean package'
    }

    stage('Archive') {
        junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
    }

}
