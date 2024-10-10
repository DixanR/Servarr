### Arrs Apps overseerr+sonarr+radarr+prowlarr+deluge

#### EDIT

- Set data volume as nfs or bind mount in compose.yml

#### Users

App | User | Group | UID | GID |
------- | ---------------- | ---------- | ----------- | ---------
supervisord | root | root | 
deluged | deluged | media | 5000 | 60000
deluge-web | deluged | media | 5000 | 60000
radarr | radarr | media | 5001 | 60000
sonarr | sonarr | media | 5002 | 60000
prowlarr | sonarr | media | 5003 | 60000

#### RUN

- docker-compose up -d --build

#### Your Configs

- Set deluge download path (/data/downloads)
- Add Apps/Indexers in Prowlarr
- Add download client (deluge) in radarr/sonarr, use compose service name for discovery
- Add media folders to sonarr/radarr (/data/{series,movie})

#### Nginx Reverse-Proxy

- Change the Url Base in "Settings->General" to /radarr /sonarr /prowlarr in the corresponding app and the following endpoints will work:
   * http://ipaddr        // Deluge
   * http://ipaddr/sonarr
   * http://ipaddr/radarr
   * http://ipaddr/prowlarr

#### ServiceName:Port

- deluged:8112
- radarr:7878
- sonarr:8989
- prowlarr:9696
- overseerr:5055
