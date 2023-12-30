# Synchronize Zotero for Free on Multiple Devices

This guide shows a way to freely synchronize and backup a Zotero library on multiple devices.
A Zotero account allows to freely backup up to 2GB of library. Alternatively, it allows to synchronize the library via a WedDav server.
This guide consists of setting up and launching a local WebDav server, in a Docker container, that stores and manages the Zotero library. The folder containing the raw-data of the Zotero library, managed by the local WebDav server, is then synchronized with a cloud storage (kdrive in this case).

Kdrive is choosen as a cloud storage provider as it offers 15GB of free storage and a synchronization app available for Windows, MacOs and Linux.

The same approach can be applied with any other cloud storage / application that enables you to synchronize a local folder with a cloud provider.

## Requirements:
- Zotero https://www.zotero.org/
- Docker https://www.docker.com/
- docker-compose
- kdrive https://www.infomaniak.com/it/kdrive
  - Create a new account, install the synchronization app, create a folder inside your cloud storage where to store the Zotero library, synchronize the folder on your machine with the dedicated app.

## Install Instructions

Based on the docker image https://hub.docker.com/r/derkades/webdav

1. Clone the repository;

`git clone https://github.com/giovannifarina/webdav_zotero.git`

2. Edit the `volume` parameter in `docker-compose.yml` and specify the path to folder containing the Zotero's data, e.g.

`volumes: ['/Users/gio/kDrive/webdav_zotero:/data']`

You can edit the other basic configuration parameters therein if you like;

3. Execute the following code

`docker-compose build`

`docker-compose -p webdav_zotero up -d`

4. Grant write permission to the volume folder to "other" 

5. Edit Zotero's settings
   1. Login with your Zotero account
   2. Below, select WebDAV
   3. Set the parameters as in the following picture
   4. Click on the verify button to check if WebDAV is properly working

6. Apply the same procedure on all the machine you would like to get synchronized. Remember to keep your synchronization app active on the folder you provided at point 2. The WebDav server should start automatically when you start Docker.

<p align="center">
    <img src="zotero_settings.png">
</p>

