### Arrs Apps overseerr+sonarr+radarr+prowlarr+deluge

#### EDIT

- Set data volume as nfs or bind mount in compose.yml

#### Users

App | User | Group | UID | GID |
------- | ---------------- | ---------- | ----------- | ---------
supervisord | root | root | 
deluged | deluged | media | 1005 | 50000
deluge-web | deluged | media | 1005 | 50000
radarr | radarr | media | 1000 | 50000
sonarr | sonarr | media | 1002 | 50000
prowlarr | sonarr | media | 1003 | 50000

#### RUN

- docker-compose up -d --build

#### Your Configs

- Set deluge download path (/data/downloads)
- Add Apps/Indexers in Prowlarr
- Add download client (deluge) in radarr/sonarr, use compose service name for discovery
- Add media folders to sonarr/radarr (/data/media/{series,movie})

#### Nginx Reverse-Proxy

- Change the Url Base in "Settings->General" to /radarr /sonarr /prowlarr in the corresponding app and the following endpoints will work:

   * http://ipaddr        // Deluge
   * http://ipaddr/sonarr
   * http://ipaddr/radarr
   * http://ipaddr/prowlarr
   * http://ipaddr/overseerr

#### ServiceName:Port

- deluged:8112
- radarr:7878
- sonarr:8989
- prowlarr:9696
- overseerr:5055

### Issues

- Hardlinks - Sonarr and Radarr copy instead of Hardlinking the content to the download client path - WorkAround - Add /usr/bin/adjust_rights.sh to Deluge execute plugin on Torrent Complete.

