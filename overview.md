comment: 'This document is only ment for briefing and should not be used for the final handin'
comment: 'The overview is taken from the explanation of each section of the online api: pomelo.netease.com/api.html'

### Application
- Aplication prototype

### BackendSessionService
- accessed by: 
```js
app.get('backendSessionService') 
```
or
```js
app.backendSessionService
```
- Created for each server process
- Maintains backend session
- Communicates with the relative frontend servers

### BackendService
- Proxy for the frontend internal session
- Should not be accessed directly
- Helps to keep key/value pairs locally
- Main operation on this should be read
- Changes are local
- Changes are dicarded on next request
- If changes should affect front end, theese should be pushed manually
- A push overwrites previous push with same key
- Transactions must be made externaly if session is pushed concurrently

### ChannelService
- accessed by:
```js
app.get('channelService')
```
- Create and maintain channels for server local 

### Channel
- Maintains the reciver collection for a subject
- Users can be added
- Broadcast messages

### SessionService
- accessed by:
```js
app.get('sessionService')
```
or
```js
app.sessionService
```
- Maintains internal session for each client connection
- Only accessible in frontend servers

