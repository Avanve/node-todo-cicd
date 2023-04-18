# Jenkins CICD with Docker, EC2 and Github Integration

# Pre-requsits

Run these commands:

  `sudo apt install nodejs`

  `sudo apt install npm`

  `npm install`

  `node app.js`

1 Create AWS EC2 instance

2 Install jenkins on EC2
    
    sudo apt update
    
    sudo apt install openjdk-11-jre

    java -version

    curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \   /usr/share/keyrings/jenkins-keyring.asc > /dev/null 
    
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \   https://pkg.jenkins.io/debian binary/ | sudo tee \   /etc/apt/sources.list.d/jenkins.list >            /dev/null

     sudo apt-get update 
    
     sudo apt-get install jenkins
     
     sudo systemctl enable jenkins

     sudo systemctl start jenkins

     sudo systemctl status jenkins

     sudo cat /var/lib/jenkins/secrets/initialAdminPassword

     history

3 Install Docker on EC2
  
     sudo apt install docker.io

4 Write Dockerfile

    FROM node:12.2.0-alpine

    WORKDIR app

    COPY . .

    RUN npm install
    

    EXPOSE 8000

    CMD ["node","app.js"]

4 Build DcokerFile

    docker build . -t node-app

    sudo usermod -a -G docker $USER
    
    sudo reboot
    
    cd /var/lib/jenkins/secrets/initialAdminPassword
    
    docker build . -t node-app-todo

    docker run -d --name node-app-container -p 8000:8000 node-app-todo
    
    docker kill cintainerId

    

5 Go to jenkins job

6 To automate docker build go to --> ADD Build Steps --> Execute shell 

     docker build . -t node-app-todo

  
     docker run -d --name node-app-container -p 8000:8000 node-app-todo
     
7 Add Webhook

    Install Webhook plugin
    
    Configure webhook on Github
    
    add webhook
    
8 Go to Confiure Jenkins --> Build Trigeers --->add Github hook triger  for Gitscm polling

When code changes webhook triggers and Jenkins build, Test and Deploy application automataically on EC2
    
    
    
    




