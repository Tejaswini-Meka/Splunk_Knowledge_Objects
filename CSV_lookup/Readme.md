### Creating CSV_Lookup.csv
To create a lookup in Splunk from a local file via the command line using PuTTY, follow the steps below. </br>

##### 1. Log in to Splunk instance via PuTTY
+ Open PuTTY and enter the IP address or hostname of your Splunk server.
+ Login with your credentials.

##### 2. Upload the CSV file to the Splunk Server

If the lookup file (e.g., a CSV file) is on your local machine, you need to transfer it to the Splunk server. You can use SCP (secure copy) 
Before connecting to the root/splunk user we have to do this.
```
scp /path/to/local_file.csv user@<splunk_server_ip>:/path/to/splunk/etc/apps/<app_name>/lookups/
```
scp "C:\Users\tmeka\Downloads\Lookups\ip_lookup.csv" root@X.X.X.X:/home/
After this type yes the connection in the terminal and give root user password.
Once logged in as a root user movew to the file located directory ``` cd /home ``` 
use below command to change the permissions of the file.

```
chmod 765 <lookup_file.csv>
```
Check the permissions of the file by entering the command ```ll ```

Now copy we have to copy the file from home directory to our lookups directly in the search app.
```
cp -r lookup_file.csv /opt/splunk/etc/apps/search/lookups
```
Now move to the lookups directory and check lookup file is existed or not
```
cd /opt/splunk/etc/apps/search/lookups
```
```
ls
```
Now you see the file in the lookup directory.

When you uploaded a file into the lookup directory in Splunk, it needs to be properly configured in order for Splunk to recognize and use it as a lookup table. This is where the transforms.conf file comes in.

Create **tranforms.conf** file in the local directory of the respective application if it is not present.

```
touch transforms.conf
```
Edit the file
```
vi transforms.conf
```
Keep below stanza in **transforms.conf**

```
[lookup_name]
filename = lookup_name.csv
```
we can restart /debug refresh the splunk
```
 /opt/splunk/bin/splunk restart
````
refresh
```
https://<IP Address of Splunk instance>:<PortNumber>/en-US/debug/refresh
```

##### If the server is existed in cloud follow below commands.

 before connecting to the instance use ```scp``` command
 ```
scp -i "Sydney_Key.pem" ip_lookup.csv ec2-user@ec2-54-66-231-19.ap-southeast-2.compute.amazonaws.com:/tmp
```
Connect to the instance
```
ssh -i "Sydney_Key.pem" ec2-user@ec2-54-66-231-19.ap-southeast-2.compute.amazonaws.com
```
Change the permissions of the file
```
chmod 765 <ip_lookup_csv>
```
check the permissions of the file
```
ll
```
Login as splunk user
```
sudo su - splunk
```
go to tmp folder as our file is located in tmp folder
```
cd /tmp
```
copy file from tmp folder to lookups folder
```
cp ip_lookup.csv /opt/splunk/etc/apps/search/lookups
```
change directory from tmp folder to lookup folder
```
cd /opt/splunk/etc/apps/search/lookups
```
list out the files existed in lookups folder

```
ls
```



