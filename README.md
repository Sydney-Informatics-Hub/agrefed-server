# agrefed-server
Public server repo instructions for AgReFed on Nimbus

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


# AWS
Public server repo instructions for AgReFed on AWS

Mostly click next. Choose ubuntu as a base image. Set root dir size to something reasonable (300gb). Check boxes to allow HTTP traffic.

Put this into the _user data_ section.

```
#!/bin/bash
sudo apt-get update
git clone https://github.com/Sydney-Informatics-Hub/AgReFed-Workshop
cd /etc/skel
sudo ln -s /home/ubuntu/AgReFed-Workshop/ AgReFed-Workshop

sudo apt install python3 python3-dev git curl
curl -L https://tljh.jupyter.org/bootstrap.py | sudo -E python3 - \
  --admin ubuntu \
  
export PATH=/opt/tljh/user/bin:${PATH}

echo "export PATH=/opt/tljh/user/bin:${PATH}" >> ~/.bashrc

conda install -y -c conda-forge ipywidgets notebook jupyter pip rasterio google-cloud-sdk rioxarray scikit-learn geopandas shapely pyreadr ipykernel ipython pyyaml rasterstats netcdf4 scipy seaborn pandas numpy matplotlib numba geopy schema termcolor

pip install alive-progress black colour coverage earthengine-api ee-extra eemont fiona folium gdown geeadd geedim geemap geocoder geographiclib geojson google-api-core google-api-python-client google-auth google-auth-httplib2 google-cloud-core google-cloud-storage google-crc32c google-resumable-media googleapis-common-protos grapheme httplib2 httplib2shim ipyfilechooser ipyleaflet joblib json5 jupyter-server jupyterlab jupyterlab-server munch nltk notebook-shim odc-stac owslib papermill pillow plotly pystac pystac-client pytest pytest-cov requests rich selectio setuptools tqdm twine wxee

```

Join the server at the instance ip address. Set a password on first join (username will be *ubuntu*).


Remove users from the control panel and delete there dirs with:
```
sudo userdel -r <jupyter-user>
```



