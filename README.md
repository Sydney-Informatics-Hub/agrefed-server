# agrefed-server
Public server repo instructions for AgReFed

```
#Identify unmounted volume
lsblk
#Format that volume
sudo mkfs -t xfs /dev/vdc
#Make a dir to mount it to and mount it
sudo mkdir /data
sudo mount /dev/vdc /data

sudo apt-get update
git clone https://github.com/Sydney-Informatics-Hub/AgReFed-DataHarvester
cd /etc/skel
sudo ln -s /home/ubuntu/AgReFed-DataHarvester/ AgReFed-DataHarvester

sudo apt install python3 python3-dev git curl
curl -L https://tljh.jupyter.org/bootstrap.py | sudo -E python3 - \
  --admin <admin-user-name> \
  
```

Join the server at the instance ip address. Set a password on first join.
Set up the environemnt required.
```
sudo -E  pip install netCDF4 rioxarray==0.10 OWSLib==0.25 numba==0.55 rasterio==1.2
sudo -E conda install --channel conda-forge gdal=3.4.2 geopandas=0.10 numpy=1.21
```

Remove users from the control panel and delete there dirs with:
```
sudo userdel -r <jupyter-user>
```
  
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

