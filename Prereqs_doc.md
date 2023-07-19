# WindowsTools

Install chocolatey from the instructions given in the link below.

https://chocolatey.org/docs/installation

```
choco install virtualbox --version=7.0.8 -y
```
```
choco install vagrant --version=2.3.4 -y
```
```
choco install git -y
```
```
choco install corretto11jdk -y
```
```
choco install maven -y
```
```
choco install awscli -y
```
```
choco install intellijidea-community -y
```
```
choco install vscode -y
```
```
choco install sublimetext3.app -y
```

# MacOS Tools

Install brew from the instructions given in the link below.


https://brew.sh/

After installing homebrew
Create a file in users home directory with name .curlrc with content “-k” 
(-k without quotes and give a new line character after -k.)

Steps:

1. OpenTerminal
2. Execute below command
```
echo -k > ~/.curlrc
```
3. Execute below command to see -k in file ~/.curlrc 
```
cat ~/.curlrc
```

Run all the below commands in Terminal


### (virtualbox command is not For MacOs M1/M2)
```
brew install --cask virtualbox 
```
```
brew install --cask vagrant
```
```
brew install --cask vagrant-manager
```
```
brew install git
```
```
brew install openjdk@11
```
```
sudo ln -sfn $HOMEBREW_PREFIX/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```
```
exec zsh -l
```
```
brew install maven
```
```
brew install --cask visual-studio-code
```
```
brew install --cask intellij-idea
```
```
brew install --cask intellij-idea-ce
```
```
brew install --cask sublime-text
```
```
brew install awscli
```


-------------



Tools Prerequisites for Ubuntu 20
                                 Tools Prerequisites for Ubuntu 20


Install Virtualbox

$ sudo apt update

$ sudo apt install virtualbox



Install Vagrant

$ curl -O https://releases.hashicorp.com/vagrant/2.2.9/vagrant_2.2.9_x86_64.deb

$ sudo apt install ./vagrant_2.2.9_x86_64.deb


Install Git

$ apt install git



Install jdk8

$ sudo apt-get install openjdk-8-jdk



Install Maven

$ sudo apt-get install maven


Install awscli

$ sudo apt-get install awscli




Install Intellij community

$ sudo snap install intellij-idea-community --classic


Install Sublime Text

$ sudo apt update

$ sudo apt install dirmngr gnupg apt-transport-https ca-certificates software-properties-common

$ curl -fsSL https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -

$ sudo add-apt-repository "deb https://download.sublimetext.com/ apt/stable/"

$ sudo apt install sublime-text


