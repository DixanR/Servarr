### *Arrs Apps sonarr+radarr+prowlarr+deluge

#### EDIT

- *Set data volume as nfs or bind mount in compose.yml 

#### Web GUI

- Set deluge download path (/data/downloads)
- Add Apps/Indexers in Prowlarr 
- Add download client (deluge) in radarr/sonarr, use compose service name for discovery
- Add media folders to sonarr/radarr (/data/{series,movie})

#### ServiceNames:Port

- deluged:8112
- radarr:7878
- sonarr:8989
- prowlarr:9696
