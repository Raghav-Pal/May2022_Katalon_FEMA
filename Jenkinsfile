pipeline {
    agent any
    stages {
         stage('Hello') {
            steps {
                echo 'Hello World'
//                 git branch: 'master', url: 'https://github.com/Raghav-Pal/May2022_Katalon_FEMA'
            }
        }
        stage('Test') {
            steps {
                dir('/var/lib/jenkins/workspace/7_RunJenkinsfileFromSCM_KatalonDockerRun'){
                    sh 'docker run -t --rm -v "$(pwd)":/tmp/project katalonstudio/katalon katalonc.sh -projectPath=/tmp/project -retry=0 -testSuitePath="Test Suites/Suite2" -browserType="Chrome" -executionProfile="default" -apiKey="3315bf05-eb56-4f10-8716-6762fb652ee4"'
                }
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'Reports/**/*.*', fingerprint: true
            junit 'Reports/*/Suite2/*/*.xml'
        }
    }
}
