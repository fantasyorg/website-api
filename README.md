# Rede Fantasy

A complete api with several solutions to manage your data or even access server data.

## User access token

All server users have an access token, consisting of a [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken), consisting of your uuid and your hash. You can get your hash by accessing the server and typing the command <code>/developer</code>.

Using your token you will get access to the api, using a header with the <code>authorization</code> in your requests.

## User API
Our server has a public API for everyone to be able to view their own or other users account information
###

 Access your own account data:
```javascript
   const response = await fetch('https://redefantasy.com/api/user', {
        headers: {
            'Content-Type': 'application/json',
            'authorization': 'ACCESS-TOKEN'
        }
   }).then(data => data.json());
   
   if (response.status == 200) {
       console.log(response.user);
       
      /* 
      {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "XXX",
        "lastJoin": "0",
        "lastQuit": "0",
        "registeredDate": "0",
        "gold": 0,
        "vanish": false,
        "group": "default",
        "online": false
       }
      */
   }
```
###
 To access information from other players, we use uuid as a search parameter, as in the example below:
```javascript
   const uuid = "00000000-0000-0000-0000-000000000000";
   
   const response = await fetch(`https://redefantasy.com/api/user/get/${uuid}`, {
        headers: {
            'Content-Type': 'application/json',
            'authorization': 'ACCESS-TOKEN'
        }
   }).then(data => data.json());
   
   if (response.status == 200) {
       console.log(response.user);
           
      /* 
      {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "XXX",
        "lastJoin": "0",
        "lastQuit": "0",
        "registeredDate": "0",
        "vanish": false,
        "group": "default",
        "online": false
       }
      */
   }
```

###
To search for multiple users at once, thus facilitating the manipulation of data, an array of uuid is used to carry out the searches, as in the example below:
```javascript
   const uuidArray = ["00000000-0000-0000-0000-000000000000", "00000000-0000-0000-0000-000000000000"];
   
   const response = await fetch(`https://redefantasy.com/api/user/getAll?users=${JSON.stringify(uuidArray)}`, {
        headers: {
            'Content-Type': 'application/json',
            'authorization': 'ACCESS-TOKEN'
        }
   }).then(data => data.json());
   
   if (response.status == 200) {
       console.log(response.users);
           
      /* 
      [
        {
            "uuid": "00000000-0000-0000-0000-000000000000",
            "name": "XXX",
            "lastJoin": "0",
            "lastQuit": "0",
            "registeredDate": "0",
            "vanish": false,
            "group": "default",
            "online": false
        },
        {
            "uuid": "00000000-0000-0000-0000-000000000000",
            "name": "XXX",
            "lastJoin": "0",
            "lastQuit": "0",
            "registeredDate": "0",
            "vanish": false,
            "group": "default",
            "online": false
        }
    ]
    */
   }
```
