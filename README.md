# DevOps Culture & Practice
<!-- > Red Hat Open Innovation Labs Enablement Material. Preparing Engineers, consultants and TSMs with all the cultural and engineering practices for life in a Residency.

![jenkins-crio-ocp-star-wars-kubes](./images/jenkins-crio-ocp-star-wars-kubes.png)

This is a collection of practices and exercises to take a learner through a four day simulated residency experience. Learners can expect to be exposed to labs practices such as [Event Storming](https://rht-labs.github.io/practice-library/practices/event-storming/), [Social Contract](https://rht-labs.github.io/practice-library/practices/social-contract/) and [Impact Mapping](https://rht-labs.github.io/practice-library/practices/impact-mapping/) among many more which can be found in our [Practice Library](https://rht-labs.github.io/practice-library/). Learners will also be exposed to `Labs CI/CD` - how we use OpenShift & Ansible in conjunction with Jenkins to automate build and deploy of a sample todolist application and its required infrastructure. -->

## Learner Outcomes
* Provide an immersive experience for students through practical application of DevOps culture using modern software development practices.

* Allow students to experience the cultural shift they need to make in order to begin a successful DevOps journey.

## Cluster Information

An OpenShift Cluster is required to complete the lab exercises. Students will receive by email (and by the instructors on site) the following information regarding the OpenShift cluster:
 - <**CLUSTER_URL**> -- Openshift Webconsole/API Server URL
 - <**APPS_URL**> -- Wildcard subdomain for the exposed applications deployed in the Cluster

## Learner Pre-requisites
The following table lists the software requirements for running the lab exercises:

 | Software | Version | Check |
 | -------- | ------- | ----- |
 | OCP CLI | v3.11 | $ oc version &#124; grep -i --color oc  <br><span style="color:red">oc </span> v3.11.0+0cbc58b |
 | Ansible | => v2.6 | $ ansible --version &#124; grep -i --color ansible <br> <span style="color:red">ansible</span> 2.7.2 <br> .... <br>|
 | NodeJS | v8.x | $ node -v <br> v8.11.3|
 | Git Installed | | $ git --version <br> git version 2.17.1|
 | Google Chrome Web Browser | (>59) | click [here](chrome://version/) if Google Chrome is your default browser else copy the link `chrome://version/` in your Chome |
 | Docker latest | Community Edition - Edge | $ docker --version <br> Docker version 18.05.0-ce, build f150324|
 | JDK | v8 | $ java -version <br>java version "1.8.0_131"<br>Java(TM) SE Runtime Environment (build 1.8.0_131-b11)<br>Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)|
 | Access to an OpenShift cluster | | `oc login -u <username> -p <password> <CLUSTER_URL>` |
 | Text editor such as Atom, IntelliJ or Visual Studio Code <br><br> (The exercises were created using `VSCode`, so the screenshots will match its layout and colour schemes) | - | - |

The lab exercises have been tested on the following operating systems
 * Fedora 29 64-bit
 * Microsoft Windows 10 Pro 64-bit
 * macOS 10.14 "Mojave"

 **NOTE**
 > You will need administrator or super user level access on your system to install the prerequisite software for all the three operating systems.
 Locked down systems with restricted accounts are not supported.

### Linux

1. Download and Install Node.js version 8.x LTS
```bash
wget https://nodejs.org/dist/latest-v8.x/node-v8.14.0-linux-x64.tar.gz
tar -xvzf node-v8.14.0-linux-x64.tar.gz -C /usr/local/
```
Edit your ***.bashrc*** file and add the ***node*** binary to your ***PATH*** environment variable
```bash
echo 'export PATH=/usr/local/node-v8.14.0/bin:$PATH' >> $HOME/.bashrc
```

2. Install OpenJDK version 1.8
```bash
dnf install java-1.8.0-openjdk-devel
```

3. Install Google Chrome version 70 or higher by downloading and running the the 64-bit RPM installer from https://google.com/chrome
```bash
dnf install google-chrome-stable_current_x86_64.rpm
```
4. Install Docker, Git and Ansible
```bash
dnf install git ansible docker
systemctl enable docker
systemctl start docker
```
5. Download and uncompress the OpenShift 3.11 client binary archive. Copy the ***oc*** binary to ***/usr/local/bin*** folder on your system
```bash
wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz
tar -xvzf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz
cp openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/oc /usr/local/bin/
chmod +x /usr/local/bin/oc
```
6. Download and install Atom text editor RPM installer from https://atom.io/download/rpm, or the Visual Studio Code RPM installer from https://code.visualstudio.com/docs/?dv=linux64_rpm
```bash
dnf install <rpm_name>
```

### macOS
1. Install HomeBrew for macOS by following the installation instructions at https://brew.sh/

2. Install Node.js version 8.x LTS using the brew command, and follow the instructions to add the **node** binary to the **PATH** environment variable.
```bash
brew install node@8
```
3. Install JDK version 1.8 for MacOS by using the installer from the Oracle website at https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

4. Install Google Chrome version 70 or higher by downloading it from https://google.com/chrome

5. Install Docker for Mac by following the instructions from https://store.docker.com/editions/community/docker-ce-desktop-mac

6. Install Git using brew
```bash
brew install git
```

7. Install Ansible using brew
```bash
brew install ansible
```
8. Download and install Atom text editor from https://atom.io/download/mac, or Visual Studio Code from https://code.visualstudio.com/docs/?dv=osx

9. Download and uncompress the OpenShift 3.11 client binary archive. Copy the ***oc*** binary to ***/usr/local/bin*** folder on your system
```bash
wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-mac.zip
unzip openshift-origin-client-tools-v3.11.0-0cbc58b-mac.zip
cp openshift-origin-client-tools-v3.11.0-0cbc58b-mac/oc /usr/local/bin/
chmod +x /usr/local/bin/oc
```

### Microsoft Windows

1. Download the 64-bit Node.js 8.x LTS Windows binary archive file from https://nodejs.org/dist/latest-v8.x/node-v8.14.0-win-x64.zip.

Extract the zip file archive under a suitable folder in the ***C:\*** drive. Make sure that your directory name does not have any spaces in it.

Add the directory where you uncompressed the zip file to the ***PATH*** environment variable, so that the ***node.exe*** and ***npm.cmd*** executable files are available in the system path.

2. Install JDK version 1.8 for Windows 64-bit by using the installer from the Oracle website at https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

Ensure that you install the JDK into a directory which has no spaces in its name. Add the ***JAVA_HOME\bin*** directory to the ***PATH*** environment variable, so that the ***java.exe*** and ***javac.exe*** executable files are available in the system path.

3. Install Google Chrome version 70 or higher by downloading it from https://google.com/chrome

4. Install Docker for Windows by following the instructions from https://hub.docker.com/editions/community/docker-ce-desktop-windows

5. Download and install Git for Windows by using the 64-bit installer from https://github.com/git-for-windows/git/releases/download/v2.20.0.windows.1/Git-2.20.0-64-bit.exe.

Follow the instructions at https://www.atlassian.com/git/tutorials/install-git#windows to install and verify your Git installation.

6. Download and install Atom text editor from https://github.com/atom/atom/releases/download/v1.33.0/AtomSetup-x64.exe, or Visual Studio Code from https://code.visualstudio.com/docs/?dv=win64

7. You will use a custom container image for running OpenShift client commands, and Ansible playbooks. You will map a directory on your local Windows system containing Ansible playbooks to a directory inside the container, and run the Ansible playbooks from within the container.

Execute the following commands to run Ansible playbooks on Windows systems:

* Pull the container image containing the tools and utilities that are required for running Ansible playbooks:
```bash
docker pull quay.io/redhat-training/do500-toolbox
```

* Launch the container:
```bash
docker run -it -v C:/do500-workspace:/home/tool-box/workarea:Z -p 8080:8080 -p 9000:9000 do500-toolbox /bin/bash
```

The ***C:/do500-workspace*** directory on your Windows system contains the lab files and Ansible playbooks for the lab exercises.

* Once you are inside the container, you can log in to the OpenShift cluster using the OpenShift ***oc*** command-line client, and launch the playbooks:
```bash
bash-4.4$ oc login -u <username> -p <password> <CLUSTER_URL>
bash-4.4$ cd workarea/enablement-ci-cd
bash-4.4$ ansible-playbook playbook.yml ...
```

<!-- 7. Download and uncompress the OpenShift 3.11 client binary archive from https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-windows.zip, and extract it under the ***C:\*** drive. Add the directory where you uncompressed the zip file to the ***PATH*** environment variable, so that the ***oc.exe*** executable files is available in the system path. -->

## Git and Containers 101
 - Git tutorial covering the basics - https://try.github.io/
 - Handy guide for those new to containers - https://developers.redhat.com/blog/2018/02/22/container-terminology-practical-introduction/

## Setup your IDE
The following plug-ins are useful for providing syntax highlighting for various lab files:
 - YAML Syntax Highlighter
 - JavaScript Syntax Highlighter
 - Vue.js
 - ESlint
 - Jenkinsfile
