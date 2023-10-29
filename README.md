
Based on the following docker image https://hub.docker.com/r/derkades/webdav

1. Clone the repository;

`git clone https://github.com/giovannifarina/webdav_zotero.git`

2. Edit the `volume` parameter in `docker-compose.yml` and specify the path to folder containing the Zotero's data, e.g.

`volumes: ['/Users/gio/kDrive/webdav_zotero:/data']`

You can edit the other basic configuration parameters therein if you like;

3. Execute the following code

`docker-compose build`