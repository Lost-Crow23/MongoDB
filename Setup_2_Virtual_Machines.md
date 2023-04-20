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

<img width="610" alt="config" src="https://user-images.githubusercontent.com/126012715/233392318-a59e995d-af02-4ac2-8881-c8f185a07fbd.png">

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

`sudo systemctl status mongod` , Checks to see if it is running `acive running` should be visible in terminal.

<img width="585" alt="Vagrant ssh db commands" src="https://user-images.githubusercontent.com/126012715/233393154-0e4fd985-3941-44ad-b9b8-183b44e43f4a.png">

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

`mongodb://192.168.56.100:27017/posts` or

`http://192.168.56.100:3000/posts` should be shown.

<h3>Final Iteration</h3>

- On `vagrant ssh app` we `cd` back to the app vm and use, 

<img width="580" alt="npm install" src="https://user-images.githubusercontent.com/126012715/233393813-4bceb586-f547-4f83-aa30-8114d18f1209.png">

`npm install` or `npm start`

`node seeds/seed.js`

`node app.js`

<img width="588" alt="vagrant_app_commands" src="https://user-images.githubusercontent.com/126012715/233394117-c7004235-fdb6-4edf-bcba-b06cd6f5bc4e.png">

- Copy the IP link onto browser and should work perfectly.

<img width="1428" alt="Final screenshot" src="https://user-images.githubusercontent.com/126012715/233394320-582ff51e-5a6b-4ae8-8046-c8701445671c.png">

<h1>MongoDB via db provision file</h1>

Now we edit our mongod.conf to initialise our IP address so we don't have to write the commands on our db git bash.

`vagrant up` to destroy the running VMs.

<h3>Step 1</h3>

- Edit our provisiondb.sh file to bypass the entering of our IP address on our git bash mongod.conf file. Use command:

`sudo sed -i 's/^\(\s*bindIp:\).*/\1 0.0.0.0/' /etc/mongod.conf`

`sudo systemctl restart mongod`

`sudo systemctl enable mongod`

<img width="806" alt="Mongod conf" src="https://user-images.githubusercontent.com/126012715/233438591-4fce7661-28b1-4cdc-9d3a-82e29d15356c.png">

This code lets you automate the IP address. This command executes the bindIP line in mongod.conf file to allow MongoDB to accept connections from any IP
address. `sed` is used to replace anything within the file. 

<h3>Step 2</h3>

- Run the provisiondb.sh script using `vagrant up` 

<h3>Step 3</h3>

- `cd` onto the app VM and on your git bash terminal. Follow the commands as above in the git bash terminal.

<h3>Final Iteration</h3>

- Copy and paste the provision.sh IP address with port 3000 and now your in the Sparta Post.

<img width="1422" alt="first sparta post" src="https://user-images.githubusercontent.com/126012715/233438996-079c21ec-43a3-4639-a877-61893d77a6e1.png">


