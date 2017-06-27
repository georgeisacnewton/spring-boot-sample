node {
    stage('Checkout') {
        git 'https://github.com/bertjan/spring-boot-sample'
        checkout scm
        name=env.BRANCH_NAME 
    }

     stage('Build') {
        sh 'mvn -B -V -U -e clean package'
    }

    stage('Archive') {
        junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
    }

    stage('parallel_build') {
        parallel(one: {
                  echo "I'm on the first branch!"
                  echo "$name"
                 },
                 two: {
                   echo "I'm on the second branch!"
                 },
                 three: {
                   echo "I'm on the third branch!"
                   echo "But you probably guessed that already."
                 })
    }
}
