pipeline {
    agent 'any'
    stages {
        stage('scm-ops') {
            steps {
                sh '''
                rm -rf *
                git clone -b main "https://github.com/redprasa/devops24.git"
                ls -ll -a
                '''
            }
        }
        
        stage('code compilation') {
            steps {
                sh '''
                ls -ll -a
                cd devops24
                ls -ll
                mvn clean
                '''
            }
        }
        
        stage('unit tests') {
            steps {
                sh '''
                ls -ll -a
                cd devops24
                ls -ll
                mvn test
                '''
            }
        }
        
        stage('codequality sonar') {
            steps {
                sh '''
                ls -ll -a
                cd devops24
                ls -ll
                mvn sonar:sonar
                '''
            }
        }
        
        stage('package') {
            steps {
                sh '''
                ls -ll -a
                cd devops24
                ls -ll
                mvn package
                '''
            }
        }
        stage('Deployment') {
            steps {
                sh '''
                ls -ll -a
                cd devops24
                ls -ll
                cd target
                ls -ll -a
                curl -uadmin:AP6YTKb34U6eCbND9Yfu6qqW1PM -T goog*.war "http://192.168.0.5:8081/artifactory/devops2424/"
                '''
            }
        }
    }
}
