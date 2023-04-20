<h1>Setup two Virtual Machines</h1>

<h3>Step 1</h3>

- Configuring our provision.sh so we don't encount any errors when we `vagrant up`.

<img width="617" alt="New_provision_2vms" src="https://user-images.githubusercontent.com/126012715/233084939-f8b72d58-99c2-472b-8fa3-a71b126ae5c4.png">

- Making sure we do not have npm start running.

<h3>Step 2</h3>

<img width="635" alt="Vagrant_configure_2_VMs" src="https://user-images.githubusercontent.com/126012715/233078949-a425ad3b-7076-4cd2-a82d-bd4798085fa3.png">

- Edit our `VagrantFile` to configure our second database using `db`.

- Change our IP addresses between the app and db so it doesn't cause conflicts.

<h3>Step 3</h3>

`Vagrant up`

- To initialise the two virtual machines as seen below.

<img width="728" alt="Virtual_app_db_running" src="https://user-images.githubusercontent.com/126012715/233079121-d901408b-b505-4174-a2a9-a56d724cff75.png">

<h3>Step 4</h3>

- Got to terminal and `ssh` onto the `app` and then `exit` then into `db` from git bash from our folder where we have the vagrant file in.

`vagrant shh app` 

- To get into the file and `ls` to check the app is under the folder.

`exit`

`Vagrant shh db`

- So when we `ls` into the vagrant ssh db, we should not have anything under that folder.

<h1>Setting up MongoDB with our VM</h1>

<h3>Step 1</h3>

- Change our xenial ubuntu to bionic in our `vagrant file` so that we have the latest updates in our operating system.

<h3>Step 2</h3>

- Use `vagrant up` to initialise both the VM in our virtual box

<h3>Step 3</h3>

- Go to git bash terminal and we SSH to our VMs.

`vagrant ssh app` and `vagrant ssh db`

<h3>Step 4</h3>

Creating another VM called DB to install MongoDB within it.

Run the following command in order in the `vagrant ssh db` file.

`sudo nano /etc/mongod.conf`

To access the configuration file within mongod and change your IP adresss to `0.0.0.0` so that it's accessible to the public and can import your personal / any specified IP address in the next step.

Run the following commands,

`sudo systemctl restart mongod` , Restarts MongoDB

`sudo systemctl enable mongod` , Enables the service

`sudo systemctl status mongod` , Checks to see if it is running `acive running` should be visible in terminal

<h3>Step 5</h3>

We now have to export our `DB_HOST` and create an environment variable.

Inside our `vagrant ssh app`

- Use `ls` to see if `app` is in the folder 
- 
- `node -v` to access the version of node
- 
- `pm2 -v` to access the version process manager
- 
- `sudo nano .bashrc` to access our bash shell environment and execute the script, to automate our tasks. 
- 
Inside the nano app file, we scroll down and add another line of code to connect our `DB_HOST` to our specified IP address in our `Vagrant file`

`export DB_HOST=mongodb://192.168.10.150:27017/posts >> ~/.bashrc`

This is our default IP address but in this case, the following IP address has been used `192.168.56.150` as it's within range.

`printenv DB_HOST` to print out the relevant exported IP address.

`source .bashrc` to update the edited nano file.

`mongodb://192.168.56.150:27017/posts` or

`http://192.168.56.150:27017/posts` should be shown.

<h3>Final Iteration</h3>

- On `vagrant ssh app` we `cd` back to the app vm and use, 

`npm install` or `npm start`

- Copy the IP link onto browser and should work perfectly.






