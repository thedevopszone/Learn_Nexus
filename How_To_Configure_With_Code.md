```
curl -u admin:xxx \
  -H "Content-Type: application/json" \
  -d '{
    "userId":     "newuser",
    "firstName":  "Max",
    "lastName":   "Mustermann",
    "password":   "password123",
    "emailAddress":"user@example.com",
    "status":     "active",
    "roles":      ["nx-repository-view-*-*"]
  }' \
  http://localhost:8081/service/rest/v1/security/users



# pypi repo anlegen
curl -u admin:xxx \
  -H "Content-Type: application/json" \
  -d '{
    "name": "my-proxy-repo",
    "online": true,
    "storage": {
      "blobStoreName": "default",
      "strictContentTypeValidation": true
    },
    "proxy": {
      "remoteUrl": "https://pypi.org/simple",
      "contentMaxAge": 1440,
      "metadataMaxAge": 1440
    },
    "negativeCache": {
      "enabled": true,
      "timeToLive": 1440,
      "contentMaxAge": 1440,
      "metadataMaxAge": 1440
    },
    "httpClient": {
      "blocked": false,
      "autoBlock": true
    }
  }' \
  http://localhost:8081/service/rest/v1/repositories/pypi/proxy
  
  
  # Docker
  curl -u admin:xxx \
  -H "Content-Type: application/json" \
  -d '{
    "name": "docker-proxy",
    "online": true,
    "storage": {
      "blobStoreName": "default",
      "strictContentTypeValidation": true,
      "writePolicy": "ALLOW_ONCE"
    },
    "proxy": {
      "remoteUrl": "https://registry-1.docker.io",
      "contentMaxAge": 1440,
      "metadataMaxAge": 1440
    },
    "dockerProxy": {
      "indexType": "HUB",
      "useTrustStoreForIndexAccess": false
    },
    "negativeCache": {
      "enabled": true,
      "timeToLive": 1440
    },
    "httpClient": {
      "blocked": false,
      "autoBlock": true,
      "connection": {
        "retries": 3,
        "userAgentSuffix": "Docker-Proxy-Nexus",
        "timeout": 60,
        "enableCircularRedirects": true,
        "enableCookies": false
      }
    },
    "docker": {
      "v1Enabled": false,
      "forceBasicAuth": true,
      "httpPort": 8082,
      "httpsPort": 8083
    }
  }' \
  http://localhost:8081/service/rest/v1/repositories/docker/proxy
```

