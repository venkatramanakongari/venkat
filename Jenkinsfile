pipeline {
    agent {
    label 'master'
    }
    stages {
        stage('Build') {
            steps {
                 sh '''
                   #Download the apache tomcat.
                    pwd
                    wget http://apache.mirror.iweb.ca/tomcat/tomcat-9/v9.0.27/bin/apache-tomcat-9.0.27.zip
                    yes | unzip apache-tomcat-9.0.27.zip
                    cd apache-tomcat-9.0.27
                    #set the psermissions of statup, shutdown and catalina script.
                    chmod 755 bin/*.sh

                '''
            }
        }
        stage('Deploy') {
            steps {
                 sh '''
                    #we will configure server.xml to bind tomcat to port 8088
                    pwd
                    sed -i 's/8080/8088/g' apache-tomcat-9.0.27/conf/server.xml

                '''
            }
        }
        stage('Startup') {
            steps {
                 sh '''
                #start tomcat
                pwd
                 sh apache-tomcat-9.0.27/bin/startup.sh

                '''
            }
        }
    }
}
