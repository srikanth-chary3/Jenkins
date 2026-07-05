## Jenkins installation on RHEL
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/rpm-stable/jenkins.repo

* Instead wget -O here we are using curl -o (because we are getting issues while adding the jenkins repo)
* The repo we added points to the jenkins urls

sudo curl -o /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/rpm-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade

### Add required dependencies for the jenkins package
* To run Jenkins, Java runtime is mandatory
sudo yum install fontconfig java-21-openjdk
sudo yum install jenkins
sudo systemctl enable jenkins
sudo systemctl daemon-reload

### Jenkins Plugins
Pipeline: stage viewer