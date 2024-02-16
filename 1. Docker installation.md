#Docker Installation (Linux)

1. Visit https://docs.docker.com/engine/install/ubuntu/
2. Install the `curl` command if not installed. 
     ``` 
     sudo apt install curl
     ```
3. Run these commands
     ```
     curl -fsSL https://get.docker.com -o get-docker.sh
     sudo sh ./get-docker.sh
     ```

4. Run post installation commands
     ```
     sudo groupadd docker
     sudo usermod -aG docker $USER
     ```

DOCKER INSTALLED !!!
