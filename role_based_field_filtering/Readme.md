# role_based_field_filtering
role-based field filtering is a mechanism that allows administrators to control which data or fields users with specific roles can access. This is particularly useful when you want to limit sensitive information or enforce data access restrictions based on user roles.</br>
- Controls visibility within events by redacting or obfuscating confidential information
  - Personal Identifiable Information(PII)
  - Protected health information (PHI) data when specific users run searches
 
#### Note: By default Role-based field filtering is turned off

### Role-based field filtering
### Switch to Splunk user
```
sudo su - splunk
```
### Navigate to Splunk local Directory
```
cd /opt/splunk/etc/system/local
```
### Create limits.conf file
```
touch limits.conf
```
### Edit limits.conf file
```
vi limits.conf
```
Keep the below mentioned stanza in **limits.conf**
```
[search]
role_based_field_filtering=true
```
Once it get enabled, restart the splunk </br>

To apply the **Role-based field filtering** now we need to work with **authorize.conf**
Open or create a local **authorize.conf** file at below splunk local directory
```
cd /opt/splunk/etc/system/local
```
```
vi authorize.conf
```
