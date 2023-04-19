<h1>Setup two Virtual Machines</h1>

<h3>Step 1</h3>

- Configuring our provision.sh so we don't encount any errors when we `vagrant up`.

<img width="635" alt="Vagrant_configure_2_VMs" src="https://user-images.githubusercontent.com/126012715/233084823-fd1e3028-51b1-432e-830f-80b9e306563d.png">

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

