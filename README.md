# agrefed-server
Public server repo instructions for AgReFed


sudo apt-get update
git clone https://github.com/Sydney-Informatics-Hub/AgReFed-DataHarvester
cd /etc/skel
sudo ln -s /home/ubuntu/AgReFed-DataHarvester/ AgReFed-DataHarvester

sudo apt install python3 python3-dev git curl
curl -L https://tljh.jupyter.org/bootstrap.py | sudo -E python3 - \
  --admin <admin-user-name> \
  --user-requirements-txt-url https://raw.githubusercontent.com/Sydney-Informatics-Hub/agrefed-server/requirements.txt \
  --showprogress-page
  
  
  
Rule
  Cutsom TCP Rule
Description 
  HTTP
Direction
  Ingress
Open Port 
  Port 
Port
  80
Remote  
  CIDR
CIDR 
  0.0.0.0/0

