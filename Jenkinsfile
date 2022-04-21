pipeline
        {

            options
            {
                // keep last 100 builds
                buildDiscarder(logRotator(numToKeepStr: '100'))

                // add timestamp
                timestamps()
            }
            agent any // run the pipeline on any available node
            stages{
             stage('SCM: code update')
            {
                    steps
                {
                    // Clean before build
                    cleanWs()
                    script
                    {
                        // checking out repository
                        git branch: 'main', 
                        url: 'https://github.com/holmansnc/Test-k6.git'
                    }
                }
            }     
                stage('Docker build')
                {
                    steps
                    {
                        script
                        {
                            // copying and building selenium base
                            docker run --rm -i grafana/k6 run --vus 10 --duration 30s - <scripts/ewoks.js
                        }
                    }
                }
                
            }

        }