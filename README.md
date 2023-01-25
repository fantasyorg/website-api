# Rede Fantasy

A complete api with several solutions to manage your data or even access server data.

## User access token

All server users have an access token, consisting of a [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken), consisting of your uuid and your hash. You can get your hash by accessing the server and typing the command <code>/developer</code>.

Using your token you will get access to the api, using a header with the <code>authorization</code> node in your requests, see an example below:
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
        "hash": "YOU ACCESS-TOKEN",
        "group": "default",
        "online": false
       }
      */
   }
```
