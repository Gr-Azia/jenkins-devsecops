pipeline {
    agent any
    stages {
        stage('Zap Proxy') {
            steps {
                    sh '''
                    docker run --rm -v /zap:/zap/wrk:rw -v /opt/hosts_zap:/etc/hosts -t owasp/zap2docker-stable zap-baseline.py -I -j \
                    -t http://gosip-app-intern-devsecops-dev.apps.lab.i3datacenter.my.id/ \
                    -r report.html \
                    -J report.json \
                    -g report.conf \
                    -z "auth.loginurl=http://gosip-app-intern-devsecops-dev.apps.lab.i3datacenter.my.id/login \
                        auth.username="user" \
                        auth.password="password""
                    mkdir /var/www/html/zapReport/pipeline${BUILD_NUMBER}/                              
                    cp /zap/* /var/www/html/zapReport/pipeline${BUILD_NUMBER}/
                    rm -rf /zap/*
                    '''
            }
        }
      
    }
}