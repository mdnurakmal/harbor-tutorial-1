# Docker convenient script

curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Install docker compose

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

# Copy the provided harbor.yml template 
cp harbor.yml.tmpl harbor.yml

# Install
sudo ./install.sh

# Download harbor online installer

wget https://github.com/goharbor/harbor/releases/download/v2.4.2/harbor-online-installer-v2.4.2.tgz 

tar zxvf harbor-online-installer-v2.4.2.tgz 

# Harbor default password
Admin: admin
password: Harbor12345

# Create certs.d folder and domain name folder

sudo mkdir /etc/docker/certs.d
sudo mkdir /etc/docker/certs.d/www.my-docker-registry.tk
sudo cp private.cert /etc/docker/certs.d/www.my-docker-registry.tk/
sudo cp ca_bundle.crt /etc/docker/certs.d/www.my-docker-registry.tk/
sudo cp private.key /etc/docker/certs.d/www.my-docker-registry.tk/
sudo service docker restart
