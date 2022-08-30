
# Description

**Remember! Your hashicorp cluster must exists when you are starting nomad jobs**

Этот пример настраивает jenkins
* --------------
* --------------

# System Requirements
* nomad_cluster


## Jenkins server

* Plugin Blue Ocean
* Plugin Docker Pipeline
* Create ssh key inside jenkins docker

ключ надо создать докере мастера и передать в агент
* `docker exec -it master ssh-keygen -t rsa -C ""` 


image = "jenkinsci/blueocean"

RUN jenkins-plugin-cli --plugins "blueocean:1.25.5 docker-workflow:1.28"

command = "/bin/bash"
args = ["jenkins-plugin-cli --plugins 'blueocean:1.25.5'"]



## Jenkins agent
for starting jenkins agent need

Create my own docker image (Dockerfile and then... ) 
* `docker build - < Dockerfile -t alexchub/jenkins-agent-ssh:latest-jdk11`
* `docker push alexchub/jenkins-agent-ssh:latest-jdk11`


allowing jenkins user to run sudo commands
RUN echo "jenkins ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
avoid typing sudo in command line
RUN echo "alias docker='sudo docker '" >> /home/jenkins/.bashrc


* Image for Dockerfile
  ```
  FROM jenkins/ssh-agent:latest-jdk11
  USER root
  ```

* Install git, sudo, vim, curl by jenkins docker client
  ```
  RUN apt-get update
  RUN apt-get install -y git sudo vim curl
  ```

* Allowing jenkins user to run sudo commands
  ```
  RUN echo "jenkins ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
  ```

* Avoid typing sudo in command line
  ```
  RUN echo "alias docker='sudo docker '" >> /home/jenkins/.bashrc
  ```



this is the most important command
CMD chmod 777 /var/run/docker.sock


## Необходимо добавить информацию о первоначальной настройке
##
##
##





# Example
## Example
### Example

* Example
  * Example
    * `Example`

Please note, you can add ` -D ` flag 


  * Remove all cluster's data
  ```
  cat <<< EOF | xargs -I{} ansible -i inventory.yml -m shell -a "systemctl stop {}; systemctl disable {}; systemctl daemon-reload; rm -rf /var/lib/{}; rm -rf /etc/systemd/system/{}.service; rm -rf /etc/{}" all
  EOF
  ```
