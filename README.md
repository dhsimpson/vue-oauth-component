# vue-oauth-component

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### Naver OAuth
If you want to use Naver OAuth, you hava must use backend when get token or user info   
Here is 'Nodejs Express BackEnd' example

```
const express = require('express')
const app = express()
const cors = require('cors');
const port = 3000

const apikey= 'YOUR_KEY';
const secretKey= 'YOUR_SECRET_KEY';
const redirectUri= 'YOUR_REDIRECT_URI';

const axios = require('axios');
app.use(cors());

// Getting token
app.get('/', async (req, res) => {
    try{
        const tokenQueryUri = `https://nid.naver.com/oauth2.0/token?grant_type=authorization_code&client_id=${apikey}&client_secret=${secretKey}&code=${req.query.code}&redirect_uri=${redirectUri}`
        const resToken = await axios.get(tokenQueryUri);
        res.json(resToken.data)
    }catch(e){
        console.error(e)
    }
})
// Getting user information
app.get('/me', async(req, res) => {
    try{
        const profile = await axios.get('https://openapi.naver.com/v1/nid/me', {
            headers: {
                Authorization: `Bearer ${req.headers.authorization.split("Bearer")[1].trim()}`
            }
        });
        res.json(profile.data)
    }catch(e) {
        console.error(e)
    }
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```
