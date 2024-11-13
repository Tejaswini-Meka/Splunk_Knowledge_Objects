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
Once logged in as a root user use below command to change the permissions of the file.

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
Once you see the file in the lookup directory we can restart /debug refresh the splunk
to restart the splunk
```
 /opt/splunk/bin/splunk restart
````
refresh
```
https://<IP Address of Splunk instance>:<PortNumber>/en-US/debug/refresh
```









