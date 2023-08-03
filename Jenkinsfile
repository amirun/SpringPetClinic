pipeline{
    agent{
        label "master"
    }
    tools{
        maven 'M3'
    }
    stages{
        stage("checkout"){
            steps{
                echo "========executing A========"
                git  branch: 'main', url: 'https://github.com/amirun/SpringPetClinic.git'
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("build_test_package") {
            steps{
                sh 'mvn compile test package'
            }
        }
        stage("deploy") {
            steps {
                sh "java -jar /var/lib/jenkins/workspace/PCDeclarativePiple/target/*.jar"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
