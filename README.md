# gifter

###
https://gifter-b50fc.web.app/

### 
https://gifter-b50fc-default-rtdb.firebaseio.com/

## Site function
```
Users can setup birthday events and invite users to organize (choose) gifts.  


├─── Event creator 
│     ├── Create event
│     │    └─ Use Oauth to verify login
│     │     └─ Generate new event page (unique url)
│     ├── Set event theme (custom message)
│     │    └─ event theme visible on landing page when not logged in
│     ├── Set event name and landing message
│     │    └─ Landing message visible without login
│     ├─ Set event date
|     ├─ Set gift list
│     │   └─ For each gift set name, description and number available (can be unlimited)
│     ├─ Set number of participants by name
│     │   └─ Use unique url for all users to access event and gift list
│     │       └─ Edit options visible when creator has logged-in
│     │       └─ When gift is choosen and 0 left, then will not be visible anymore
│     │   └─ Email event link and link for copying
│     ├─ Delete event
│     │   └─ Ask are you sure
│         └─ Replace event page with landing page (deleted) on same url
│ 
│ 
│ 
└──┬─ Event participant
   ├─ Get email invite link with unique url to the event
   ├─ Choose the gift
   ├─ Get (email) verification of the gift chosen and event
   
```

## Site layout
```
├───┬─ Main page (index)
│   ├─ Go to event (module on main page)
│   ├─ Create event (module on main page)
│   ├─ Login module with Oauth verification (so when going to event page you are logged in)
│       └─ track login status with cookie
│
├──── Event page (unique, auto generated)
│       └─ Landing page if user is not logged in, offer log in
│       └─ 404 if event not created
│       └─ Landing page "deleted by user" if event was created but deleted
├──── 404 page (redirect in 5 sec to index)
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

Email sending: https://www.freecodecamp.org/news/send-emails-from-your-vue-application/

Oauth use: https://fusionauth.io/blog/2020/08/06/securely-implement-oauth-vuejs/

CRUD operations: https://grokonez.com/firebase/vue-js-firebase-database-example-crud-operations
