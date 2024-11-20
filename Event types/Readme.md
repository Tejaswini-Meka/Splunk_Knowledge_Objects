## Event Types
Event types are a categorization system to help you make sense of your data. Event types let you sift through huge amounts of data, find similar patterns, and create alerts and reports
example:
```
sourcetype=access_combined status=200 action=purchase
```
- we can create an eventtype from this, search will basically gives us info about all the **"successful purchases"**.
- After Event type creation, any event which will satisfy the above condition will be assigned the Event type in search time.
- The single event can match the multiple Event types, when an event matches two or more event types, event types act as multi-value field.
- It is not recommended to use event types to shorten a portion of a search, as it can consume a lot of data.
- More Event types, more the cost in search performance.
- If you want to shorten a portion of search, better to use search macros in those cases.

#### Restriction
- Search string that define event types cannot reference tags
- Search string cannot include pipe operator
- Search string cannot include subsearch
- It is recommended that you should not defined an event type by a simple search that uses the saved search command to reference a report time</br>

**Example:**
  If you have a report named ```failed_login_search```, you should not use this search to define the</br>
  event type: ```| savedsearch failed_login_search```. In this case you should instead use the search string that defines 
  ```failed_login_search``` as the definition of the event type.

#### Creating Event types:

**1. From Search bar**
![image](https://github.com/user-attachments/assets/6161ac45-076f-41b5-a8b0-29e1c983f0fd)

![image](https://github.com/user-attachments/assets/f580392a-c6e6-48c0-b8b0-fce51d39fc69)

**2. From events**
![image](https://github.com/user-attachments/assets/77831b42-aa31-4060-9193-61f42d0b24e2)

**3. From Settings-> Knowledge -> Event types -> New Event Type**
![image](https://github.com/user-attachments/assets/5e74ed9d-c932-4a89-b649-01ecf17d17c8)

![image](https://github.com/user-attachments/assets/46980ea1-4735-4d8c-8c02-260232719d9f)

#### Filling the details

![image](https://github.com/user-attachments/assets/588f8c3d-dade-4545-9ac3-b6dfe2e67353)

Whatever the event is matching with our event type will be reflect in mentioned colour

![image](https://github.com/user-attachments/assets/35f912a1-6ab5-4e5d-a246-420c4bea8d28)

Priority field takes the precedence of the event type.
Suppose same event is matching with two event types then based on the precedence it will show the event types.

As our event type priority is highest, it is showing at first.

![image](https://github.com/user-attachments/assets/a5bf2d92-10b3-4ab4-83d0-7620162469e4)


same can be done from **"eventtypes.conf"** file of the respective app local directory

```
[YOUR_EVENTTYPE_NAME]
disabled = <1|0>
search = <string>
description = <string>
priority = <integer>
color = <string>
```

It will be like

```
Malformed_signature
disabled = 0
search = index=gss_syslog_waf Attack_Name=MALFORMED* Severity=ALER
prioriy = 1
color = et_green
```

Dynamic configurations will be like

```
[%Attack_Name%-signature]
disabled = 0
search = index=gss_syslog_waf  Severity=ALER
prioriy = 1
color = et_green
```

so whatever the value we are getting under Attack_Name, event type is going to get created for the same.




