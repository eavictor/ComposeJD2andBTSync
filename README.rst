==================================
Cloud JDownloader and Resilio Sync
==================================

This Compose File is for satisfying my need for downloading and automatically sync downloaded files across
**Pacific Ocean** automatically.

-------------
Docker images
-------------

`JDownloader 2`_ : Docker image packed by jaymoulin

.. _JDownloader 2: https://hub.docker.com/r/jaymoulin/jdownloader

`Resilio Sync`_ : Docker image packed by Resilio (official image)

.. _Resilio Sync: https://hub.docker.com/r/resilio/sync/

-------
Install
-------

.. _MyJDownloader: https://my.jdownloader.org/

1. Go to MyJDownloader_ register an account if you don't have one.

2. Install docker

.. code-block:: shell

    sudo bash ./install_docker.sh username

3. create folders (bind mount between host & containers)

.. code-block:: shell

    cd /home
    mkdir downloader
    cd downloader
    mkdir jd2cfg folders
    cd folders
    mkdir jd2dl

4. Switch back to the folder you cloned from GitHub (this folder)

5. Deploy docker containers by using compose

.. code-block:: shell

    docker-compose -f docker-compose.yml up -d

6. Get the name of JDownloader2 container, the name should contain "jd2".

   Name of JD2 container will be something like ``cloud_downloader_jd2_1``

   I will use ``cloud_downloader_jd2_1`` for example

.. code-block:: shell

    docker container ls

7. Configure JDownloader with registered MyJDownloader username and password. 2nd line is example.

.. code-block:: shell

    docker exec <jd2_container> configure <username> <password>

.. code-block:: shell

    docker exec cloud_downloader_jd2_1 configure example@google.com mypassword

8. Configure Resilio Sync : Open your browser and follow official guide adding ``jd2dl`` as one of your sync folder.

9. Configure JDownloader2 on MyJDownloader_