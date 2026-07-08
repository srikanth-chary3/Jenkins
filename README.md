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

### Adding disk space to the jenkins home directory for master and the slave nodes
Partition the disk
growpart /dev/nvme0n1 4

lvextend -L +10G /dev/mapper/RootVG-varVol
lvextend -L +10G /dev/mapper/RootVG-rootVol
lvextend -l +100%FREE /dev/mapper/RootVG-homeVol

xfs_growfs /
xfs_growfs /var
xfs_growfs /home

### Jenkins Plugins
Pipeline: stage viewer
GitHub


### Master Agent Architecture

* Create credentials to connect agent
* Install Java in agent
* Select Non verification strategy