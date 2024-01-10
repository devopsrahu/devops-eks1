pipeline {
    agent any

   stages {
          stage('aws cred') {
            steps {
               withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: "9f535483-188c-4e51-84d0-41a073f6f7f4",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    sh 'aws ec2 describe-instance'
                }
            }
        }
    
         stage('init') {
            steps {
                sh 'terraform init'
            }
        }
         stage('validate') {
            steps {
                sh 'terraform validate'
          }
        }
         stage('plan') {
            steps {
                sh 'terraform plan'
         }
       }
         stage('apply') {
            steps {
                sh 'terraform apply --auto-approve'
        }
      }
      /*  stage('destroy') {
            steps {
                sh 'terraform destroy --auto-approve'
        }
      }*/

}
}
