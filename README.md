Use these steps for
SQLite Error 5: 'database is locked and SQLite Error 11: 'database disk image is malformed'

NOTE: I Used this in a Proxmox LXC (deb) for jellyfin when my DB was locked and once when it was malformed. 

CD into your dabase folder Default is /var/lib/jellyfin/data

Step 1)Extract db

> sqlite3 jellyfin.db ".dump" > data.sql

Step2) Rename old db

>mv jellyfin.db jellyfin2.db

Alternitivly you can use WinCP to tunnel into your host server and rename it that way

Step 3)Rebuild DB

> sqlite3 jellyfin.db < data.sql

Step4) Change permissions 

> chmod 777 (or 755) jellyfin.db

NOTE: If you get error "SQLite Error 8: 'attempt to write a readonly database" after permissions change you may need to do a change of onership for the DB file

>chown jellyfin:jellyfin jellyfin.db
