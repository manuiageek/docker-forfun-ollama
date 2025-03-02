# PREREQUISITES

## install Ubuntu in wsl2 and set version 2 by default

wsl install
wsl --set-version Ubuntu 2

## install nvidia toolkit

wsl
sudo rm -f /etc/apt/sources.list.d/nvidia-docker.list
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
distribution=ubuntu22.04
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt update
sudo apt install -y nvidia-docker2

## restart docker

sudo systemctl restart docker
docker run --rm --gpus all nvidia/cuda:12.0.0-base-ubuntu22.04 nvidia-smi
dpkg --print-architecture

# CREATE VOLUME in docker

docker volume create ollama_data

# Interesting Ollama models to use with RTX 3070 Graphic Card :

ollama pull [insert_your_favorite_model_here]
qwen2.5-coder:1.5b-instruct-q8_0
llama3.2:3b-instruct-q8_0
deepseek-r1:8b-llama-distill-q4_K_M
llama3.1:8b-instruct-q5_K_M
