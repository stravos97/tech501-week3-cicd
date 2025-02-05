![](Pasted%20image%2020250205123814.png)
Use your current ssh key

Use ireland for all info



![](Pasted%20image%2020250205132452.png)

Set the VM as t.3 micro
and select Ubutntu 22.0.4
Take a note of the instance username e.g. `ubuntu`
![](Pasted%20image%2020250205131243.png)
and allow SSH and HTTP traffic. SSH for testing , it will be disabled later

Click `Launch instance` and then find the public IP address

![](Pasted%20image%2020250205132740.png)

So we can ssh into it. In this case:
```bash
ssh ubuntu@63.33.65.145
```
Note the username of the instance is set when we createed the VM


Once we have SSH'd in we are following the same steps as before, namely:

1. Update the system
2. Install and configure Mongodb
3. 


**Install Mongo DB**

![](Pasted%20image%2020250205140451.png)

**Configure MongoDB**

Set the bindIP
![](Pasted%20image%2020250205140828.png)

![](Pasted%20image%2020250205140932.png)


5. **Enable and Restart MongoDB:**
    
    
    `sudo systemctl enable mongod` 
    `sudo systemctl restart mongod` 
    `sudo systemctl status mongod`
    
    - **Explanation:**
        - `enable mongod`: Ensures MongoDB starts on system boot.
        - `restart mongod`: Restarts the MongoDB service to apply configuration changes.
        - `status mongod`: Checks if MongoDB is running correctly.

![](Pasted%20image%2020250205155138.png)

Enable access to the Mongodb port so the Sparta App can communicate to the DB using it's vnet ip adrress
### Deploying the Application
![](Pasted%20image%2020250205141859.png)

![](Pasted%20image%2020250205141530.png)
Enable port 3000
![](Pasted%20image%2020250205145232.png)

![](Pasted%20image%2020250205145440.png)

We are then SSH'ing into the new one:

```bash
ssh ubuntu@34.253.228.178
```
Once logged in, update the system again

Then follow the process of

1. Install NGINX
2. Install node
3. Setup the reverse proxy

**Intstall NGINX**

3. **Install NGINX:**
    
    - NGINX will serve as a web server and reverse proxy.
        
        
        `sudo apt-get install nginx -y` 
        `sudo systemctl status nginx`
        
        - **Explanation:**
            - `apt-get install nginx`: Installs the NGINX web server.
            - `systemctl status nginx`: Checks the status of the NGINX service to ensure it's running.

![](Pasted%20image%2020250205142759.png)

Setup the reverse proxy on port 3000:
![](Pasted%20image%2020250205150043.png)
Edit this file
```bash
sudo vi /etc/nginx/sites-available/default
```

and set:
```bash
proxy_pass http://localhost:3000;
```
then restart nginx:
```bash
sudo systemctl restart nginx
```


**Install Node & NPM**

4. **Install Node.js and NPM:**
    
    - Node.js is a JavaScript runtime, and NPM is its package manager.
        
        
```bash
        sudo apt-get install npm
        npm -y 
        node -v 
        npm -v
```

```bash
sudo DEBIAN_FRONTEND=noninteractive bash -c "curl -fsSL [https://deb.nodesource.com/setup_20.x](https://deb.nodesource.com/setup_20.x "https://deb.nodesource.com/setup_20.x") | bash -" && \

sudo DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs
```
        
        - **Explanation:**
            - `node -v`: Displays the installed Node.js version.
            - `npm -v`: Displays the installed NPM version.




I'm currently using npm -v `8.5.1`, and node -v `v12.22.9`

If you get this error:
![](Pasted%20image%2020250205144216.png)

the node was the wrong version, it needs to be uninstall and built from source again

![](Pasted%20image%2020250205151824.png)
You then need to export the DB host as an environmental variable for the sparta app to query the DB

```bash
export DB_HOST=mongodb://172.31.48.7:27017/posts
printenv DB_HOST
```
If it's been set correctly, it should be printed out

You can now access the DB page