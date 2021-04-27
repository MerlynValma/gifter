# gifter

###
https://gifter-b50fc.web.app/

### 
https://gifter-b50fc-default-rtdb.firebaseio.com/

## Site function
```
Users can setup birhday events and invite users to plan for gifts. 


├─────┬─ Event creator
│     ├── Create event
│     │    └─ Use Oauth to verify login
│     ├── Set event name
│     │    └─ Generate new event page
│     │    └─ Landing message visible without login
│     ├─ Set event date
│     ├─ Set number of participants by name
│         └─ Generate unique password for each user event access
│         └─ Email event link
│ 
│ 
│ 
│ 
└───┬─ Event participant
    ├─ Get email invite link with password 
```
https://www.freecodecamp.org/news/send-emails-from-your-vue-application/

https://fusionauth.io/blog/2020/08/06/securely-implement-oauth-vuejs/



## Site layout
```
├─┬─ Main page
│ ├─ Go to event
│ ├─ Create event
│ ├─ Login with Oauth verification (so when going to event page you are logged in)
│     └─ track login status with cookie

├─┬─ Event page (unique, auto generated)
│ └─ Landing page if user is not logged in, offer log in
│ └─
```

## Source architecture

```
Vue.js 2 frontend

gifter
├─┬ frontend
│ ├── src
│      ├─ components
│          ├─
│
│
│ CLIENT
│─┬ index (SPA)
│ ├─ all events
│ ├─ create event
│ ├─ join event (password)

```
