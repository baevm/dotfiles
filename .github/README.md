# dot files

1. **basics**
```
sudo apt update && sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common \
    git \
    make \
    tig \
    tree \
    zip unzip \
    zsh
```

2. **github cli**
```
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null

sudo apt update
sudo apt install gh

gh auth login
```

3. **zsh**
```
# verify zsh installation
zsh --version
   
# Set the default shell to zsh
sudo chsh -s $(which zsh) $(whoami)
   
# Install oh-my-zsh: https://ohmyz.sh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   
# Install Powerlevel10k: https://github.com/romkatv/powerlevel10k
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

#Set `oh-my-zsh` theme to Powerlevel10k by setting the following in your `~/.zshrc`:
ZSH_THEME="powerlevel10k/powerlevel10k"

#Install the recommended font: https://github.com/romkatv/powerlevel10k#manual-font-installation
```

4. **docker**
```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg

sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo docker run hello-world
```

5. **nodejs**
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash

nvm install node
```

6. **golang**
```
goVersion=1.20.5
curl -L "https://golang.org/dl/go${goVersion}.linux-amd64.tar.gz" > /tmp/go${goVersion}.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf /tmp/go${goVersion}.linux-amd64.tar.gz
rm /tmp/go${goVersion}.linux-amd64.tar.gz

# Add go path ~/.zshrc
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH

# Update shell
source ~/.zshrc
```