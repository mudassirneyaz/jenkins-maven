pipeline {
    agent any
    parameters {
        choice(name: 'ServerType', choices:['WAS', 'BAW', 'SOA'], description: 'Enter the type of server')
        booleanParam(name: 'InstallDMGR', defaultValue: false, description: 'Do you need to install DMGR?')
        booleanParam(name: 'InstallNode', defaultValue: false, description: 'Do you need to install Node?')
        booleanParam(name: 'InstallFull', defaultValue: true, description: 'Do you need to install All?')
    }

    stages {
        stage('Init') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Select Server Type')
        {
            steps{
                script{
                    if (params.ServerType == 'WAS') {
                                            echo "WAS is getting installed"
                            return
                        
            
            } else if (params.ServerType == 'BPM') {
                
                    echo "BPM is getting Installed"
                    return
                            
        }
        else {
            
                echo "SOA is getting installed"
            
            
        }
            }
            }
        
        }
        stage('DMGR') {
            when{
                    expression{
                        (params.InstallDMGR == true && params.InstallFull == false)
                    }
                }
            steps {
                echo 'Installing DMGR'
            }
        }
        stage('Node') {
            when{
                    expression{
                        (params.InstallNode == true && params.InstallFull == false)
                    }
                }
            steps {
                echo 'Installing Node'
            }
        }
        stage('All') {
            when{
                    expression{
                        params.InstallFull == true
                    }
                }
            steps {
                 echo 'Installing All'
            }
        }
    }
}
