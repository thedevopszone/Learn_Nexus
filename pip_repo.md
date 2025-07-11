# Nexus Pip Repo


## Install Python

```
sudo dnf update -y

sudo dnf install -y python3

curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py

```



## Config Non Root

vi ~/.netrc
```
machine nexus.softxpert.duckdns.org
  login admin
  password xxx
```

vi .config/pip/pip.conf
```
[global]
index-url = https://nexus.softxpert.duckdns.org/repository/pypi-proxy/simple

#index-url = https://admin:xxx@nexus.softxpert.duckdns.org/repository/pypi-proxy/simple
```



## Global

vi /etc/pip.conf
```

```



## Install

vi requirements.txt
```
flask==2.3.3
requests>=2.31.0
numpy
pandas==2.2.2
scipy==1.13.0
matplotlib==3.8.4
sqlalchemy>=2.0
gunicorn==22.0.0
flask-cors==4.0.0
python-dotenv>=1.0.1
```

```
pip install -r requirements.txt
```



## Nexus Repo




