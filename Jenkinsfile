node('MAVEN_JDK8') {
    stage('version control') {
        git url: 'https://github.com/awsdevops210/game-of-life.git',
        branch: 'scripted'
    }
    stage('build the code') {
        sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
    }
    stage('achive the artifacts') {
        archiveArtifacts onlyIfSuccessful: true,
               artifacts: '**/target/gameoflife.war',
               allowEmptyArchive: false
    }
    stage('show the test results') {
        junit testresults: '**/surefire-reports/TEST-*.xml',
              allowEmptyResults: true
    }
}