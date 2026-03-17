pipeline{

    agent any

    tools{
        maven 'Maven 3.9.12'
    }

    stages{
        stage('build'){
            steps{
                sh 'mvn compile -Dmaven.compiler.source=17 -Dmaven.compiler.target=17'
            }
        }
        stage('test'){
            steps{
                sh 'mvn clean test -Dmaven.compiler.source=17 -Dmaven.compiler.target=17'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package -DskipTests -Dmaven.compiler.source=17 -Dmaven.compiler.target=17'
            }

            post {
                success {
                    archiveArtifacts '**/target/*.jar'
                }
            }
        }
    }
}