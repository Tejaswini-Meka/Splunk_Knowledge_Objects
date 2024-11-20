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

**2. From events**
![image](https://github.com/user-attachments/assets/77831b42-aa31-4060-9193-61f42d0b24e2)

**3. From Settings-> Knowledge -> Event types**
![image](https://github.com/user-attachments/assets/5e74ed9d-c932-4a89-b649-01ecf17d17c8)




