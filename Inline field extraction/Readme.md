### Inline Field Extractions
Inline field extractions are field extractions that are configured within props.conf.You can have one regular expression per field extraction configuration

Use inline field extractions when you:
- Have one regular expression per field extraction configuration
- Have a simple setup with one regular expression, and you want to extract multiple fields
- Want to create a new field by configuring an extraction

#### Configure an inline search-time field extraction
Inline search-time field extractions use the EXTRACT extraction configuration in props.conf. Each EXTRACT extraction stanza contains the regular expression to extract fields at search time.

Access to the props.conf located in
```
/opt/splunk/etc/system/local/
```
or in your custom app directory in 
```
/opt/splunk/etc/apps/<custom_app>/local/
```
**props.conf**
```
[your_sourcetype_here]
EXTRACT-somename = your_regex_here
```
**Example:**
```
[demo_logs]
EXTRACT-ip_address = (?<ip_address>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})

[demo_logs]
EXTRACT-time_stamp = (?<timestamp>\d{2}/[A-Za-z]{3}/\d{4}:\d{2}:\d{2}:\d{2})

[demo_logs]
EXTRACT-response_time = (?<response_time>\d+\.\d{3})
```
