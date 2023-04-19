<h1>MongoDB Provisioning</h1>

Created a VM called db and install MongoDB inside it

<h3>Using these commands as follows:</h3>

Onto our git bash terminal as did the `vagrant up` earlier.

- Onto the folder containing the vagrant file.

`vagrant shh db`

<h3>Command in order:</h3>

`sudo apt update -y` 

`sudo apt upgrade -y`

`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927`

- This key command used to import GPG key from a keyserver. Verifies the authencity and integrity of package before installing it on the system. Trust the 
key and any package we download that is signed with it. 

`echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list`

- Adds a new package repository for MongoDB to the system's package sources, to find and install MongoDB packages.

`sudo apt update -y`

`sudo apt upgrade -y`

`sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20`

- Downloads and installs the latest version of MongoDB
