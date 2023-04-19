<h1>MongoDB Provisioning</h1>

Created a VM called db and install MongoDB inside it.

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

<h2>MongoDB provisioning our db</h2>

<h3>Step 1</h3>

- `Vagrant destroy` the previous virtual box running both app and db

We create a new provision called provisiondb.sh so it's different to the original provision.

<img width="1434" alt="make folder provision" src="https://user-images.githubusercontent.com/126012715/233112541-67bb0fda-188f-4d33-ab48-73a87fe8a37a.png">

And we include the following commands as above to install MongoDB.

<img width="831" alt="New_provisiondb" src="https://user-images.githubusercontent.com/126012715/233112610-43613d66-b715-44b8-b508-4302f2587cbc.png">

- Since we used a different provision file we alter the name so we can use in our admin host folder, virtualisation, but if you want the continunity, 
of the previous provision, we can alter the path to our environment folder so that both `provision.sh` can be included.
- But we use `provisiondb.sh`

<h3>Step 2</h3>

- Now we navigate to the VS code terminal and inside the virtualisation folder we `vagrant up db` to only run the db VM.

<h3>Final Iteration</h3>

- Go on terminal and check if we have the most updated MongodDB application installed in our db VM. 

<img width="579" alt="New_provisioning_mongodb" src="https://user-images.githubusercontent.com/126012715/233116643-499157ec-88ba-4c0f-bc7e-310350ad57e2.png">

`sudo systemctl status mongod`

- `Active (running)` should be stated in the git bash terminal.

<img width="731" alt="DB_VM_provisioning" src="https://user-images.githubusercontent.com/126012715/233116680-98925b3f-4e21-4dff-a10a-6076c31c0369.png">




