pipeline{
    agent any

    stages{
        stage("build"){
           steps{
                
               sh  """
                    sudo ssh -i /var/lib/jenkins/jenkins.pem -t -o StrictHostKeyChecking=no ubuntu@ec2-13-41-162-4.eu-west-2.compute.amazonaws.com << EOF
                    cd /var
                    sudo rm -rf html
                    sudo mkdir html
                    sudo chown -R jenkins:jenkins html/
                    cd /var/html
                    sudo git clone https://github.com/Jadesolax/bitblog.git . 
                    sudo docker build -t bitblog:2 .
                    sudo docker run -d -p 80:80 bitblog:2
                    <<EOF
                    """
               
            
               


           }
            
        }


        stage("get"){
            steps{
                echo "get stage"
            }

        }


        stage("production"){

            steps{
                echo "Production"
            }
        }



    }


}