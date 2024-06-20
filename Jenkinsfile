pipeline {
    agent any
    triggers { cron('* * * * *') }
    options { timeout(time: 5) }
    parameters {
        booleanParam(name: 'DEBUG_BUILD', defaultValue: true,
        description: 'Is it the debug build?')
    }
    stages {
        stage('Example') {
            environment { NAME = 'Mateusz' }
            when { expression { return params.DEBUG_BUILD }
            }
            steps {
                echo "Hello from $NAME"
                script {
                    def browsers = ['chrome', 'firefox']
                    for (int i = 0; i < browsers.size(); ++i) {
                        echo "Testing the ${browsers[i]}."
                    }
                }
            }
        }
    }
    post { always { echo 'I will always say Hello again!' } }
}
