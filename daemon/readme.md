## Run node js app as a linux daemon

### Pre Requisite
- You have root access to your linux system 


### Node JS Specific 
- Install node js : `sudo yum install node -y`
- Verify installation : `node -v`
- Run node application : `node app.js`


### Create Daemon
- Use root : `sudo -i` or `su -`
- Go to service : `cd /usr/lib/systemd/system`
- Copy and rename existing service: `cp /usr/lib/systemd/system/crond.service /usr/lib/systemd/system/myapp.service`
- Update the content, you can refer to myapp.service in this repo, make sure you point the app.js location correctly, in this scenario, my app is in this location `/home/student/myapp/app.js`
- Verify service : `systemctl status myapp`
- Enable service : `systemctl enable myapp`
- Reload daemon : `systemctl daemon-reload`
- Start service : `systemctl start myapp`

### Expose the port 
This is important so that the application can be accessible, in this scenario I am using default node port which is 3000

- Execute following command to expose port 3000 : 
 - `firewall-cmd --permanent --add-port=3000/tcp`
 - `firewall-cmd --reload`
