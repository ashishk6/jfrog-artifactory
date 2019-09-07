# jfrog-artifactory
# Jenkins pipelines to add file in Jfrog Artifactory
> Here we will use the Docker compose file where we will have two services Jfrog Artifactory and the Jenkins pipleline using which we will add file to the Artifact repository.

-- Steps to Bring up the Jenkins and JFrog Applications:
- Write a docker compose file keepping both the Application services under same network.
- For more details please refer the Docker-compose.json
- Here we will create Docker Swarm to run this compose file:
 -- docker swarm init --advertise-addr <localhost IP>
 -- docker stack deploy -c docker-compose.json <stack name>
> This will bring up both the Jenkins and JFrog container as a services in two different host. 

> To get the Jenkins initialAdminPassword use the below command  

  - docker exec <jenkins process id> cat /var/jenkins_home/secrets/initialAdminPassword
  - Create a Generic Artifact repository Sample1 in JFrog and use the below Jenkins pipeline script to upload a sample file into the repository.
 >touch sample-test.txt
echo "hello world" >> sample-test.txt
> curl -u admin:password -T ./sample-test.txt "http://ip172-18-0-11-blpqud8nddr000fr8nk0-8086.direct.labs.play-with-docker.com/artifactory/sample1/"

-- The same upload can be done using the Artifactory name instead of passing the URL. However, both the application should run on the same network.

> curl -u admin:password -T ./sample-test.txt "http://artifactory:8081/artifactory/sample1/"

--  Use the below link for looking into the documentation:
#  [JFrog](https://www.jfrog.com/confluence/display/RTF) |  [Jenkins](https://jenkins.io/doc/) | [Github Pipeline](https://docs.gitlab.com/ee/ci/pipelines.html) 



> Note: Try to grab the understanding via hands-on. This will no only help you getting the concept but also help you to understand the flow and process.
 

