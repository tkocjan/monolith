#!/usr/bin/groovy
@Library('github.com/fabric8io/fabric8-pipeline-library@master')
def appName="ticketmonster"
def project=""


mavenNode {
    checkout scm

    container(name: 'maven') {
        stage('Build Release'){
            mavenCanaryRelease {
                skipTests = true
                useContentRepository = false
                runBayesianScanner = false
            }
//            sh "mvn clean -e -U package -Pmysql,openshift -Dmaven.test.skip=true"
        }
    }
}



//
//node("maven") {
//    stage 'checkout'
//    git url: 'https://github.com/christian-posta/ticket-monster.git', branch: 'monolith-master'
//
//    stage 'build-war'
//    dir('demo'){
//        sh "mvn clean package -Pmysql-openshift"
//        stash name:"build-context", includes:"target/openshift/**"
//    }
//
//    stage 'build-docker'
//    unstash name:"build-context"
//    sh "oc start-build ${appName} --from-dir=target/openshift --follow"
//
//    stage 'deploy'
//    openshiftDeploy deploymentConfig: appName
//}