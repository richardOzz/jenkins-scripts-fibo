
Skip to content
Pull requests
Issues
Marketplace
Explore
@richardOzz
LinkedInLearning /
essential-jenkins-2468076
Public

Code
Issues
Pull requests
Actions
Projects
Security

    Insights

essential-jenkins-2468076/Ch03/03_03-run-scripts-from-the-pipeline/Jenkinsfile
@managedkaos
managedkaos Update files for 03_03
Latest commit eddd08c on 16 Mar
History
1 contributor
40 lines (40 sloc) 1.03 KB
pipeline {
    agent any
    parameters {
        choice(name: 'NUMBER',
            choices: [10,20,30,40,50,60,70,80,90],
            description: 'Select the value for F(n) for the Fibonnai sequence.')
    }
    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, unit: 'HOURS')
        timestamps()
    }
    triggers {
        cron '@midnight'
    }
    stages {
        stage('Make executable') {
            steps {
                sh('chmod +x ./scripts/fibonacci.sh')
            }
        }
        stage('Relative path') {
            steps {
                sh("./scripts/fibonacci.sh ${env.NUMBER}")
            }
        }
        stage('Full path') {
            steps {
                sh("${env.WORKSPACE}/scripts/fibonacci.sh ${env.NUMBER}")
            }
        }
        stage('Change directory') {
            steps {
                dir("${env.WORKSPACE}/scripts"){
                    sh("./fibonacci.sh ${env.NUMBER}")
                }
            }
        }
    }
}
Footer
© 2022 GitHub, Inc.
Footer navigation

    Terms
    Privacy
    Security
    Status
    Docs
    Contact GitHub
    Pricing
    API
    Training
    Blog
    About

essential-jenkins-2468076/Jenkinsfile at main · LinkedInLearning/essential-jenkins-2468076
