## Jenkins installation on RHEL
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/rpm-stable/jenkins.repo
sudo yum upgrade

### Add required dependencies for the jenkins package
* To run Jenkins, Java runtime is mandatory
sudo yum install fontconfig java-21-openjdk
sudo yum install jenkins
sudo systemctl daemon-reload

### Jenkins Plugins
Pipeline: stage viewer