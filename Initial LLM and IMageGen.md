1.Setup WSL (Windows)

# Install WSL and Ubuntu

wsl --install

# Connect to a WSL Instance in a new window

wsl -d Ubuntu

2. Install Ollama

https://ollama.com/download

# Add a model to Ollama
ollama pull dolphin-llama3

 

Optional: "Watch" GPU Performance

watch -n 0.5 nvidia-smi

 

3.Install Docker für UI 

# Add Docker's official GPG key:

sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:

echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

#Install Docker

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

Run Open WebUi Docker Container

sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main

 

Stable Diffusion Install
Prereqs
Pyenv
#Install Pyenv prereqssudo apt install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev git

#Install Pyenv

curl https://pyenv.run | bash

#Install Python 3.10

pyenv install 3.10

#Make it global

pyenv global 3.10

 

Install Stable Diffusion
wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh

# Make it executable

chmod +x webui.sh

#Run it

./webui.sh --listen --api
