# Nexus Pip Repo


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



