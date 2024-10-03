### *Arrs Apps sonarr+radarr+prowlarr+deluge

#### EDIT

- *Set data volume as nfs or bind mount in compose.yml 

#### Web GUI

- Set deluge download path (/data/downloads)
- Add Apps/Indexers in Prowlarr 
- Add download client (deluge) in radarr/sonarr, use compose service name for discovery
- Add media folders to sonarr/radarr (/data/{series,movie})

#### ServiceNames

deluged:
    port: 8112
radarr:
    port: 7878
sonarr:
    port: 8989
prowlarr:
    port: 9696
