## Check-rs-json

### BASE ON CONFIG MOCHA TEST PLUGIN

### About

Depending on the configurable API testing framework, no coding, just config

### Example

```
git clone https://github.com/TimLiu1/check-rs-json.git
npm install
cd server && node index.js
mocha test/
```

### Example

#### Quick Study

all test demo in the [check-rs-json](https://github.com/TimLiu1/check-rs-json.git)

```
npm install check-rs-json

```

Check response string object

```js
//response
{
    code: 200,
    name: "jsoncheck"
}
const CR = require('check-rs-json')
let rules =  {
    "name":"oneSting",
    "data":[{
        "name":"oneSting check value",
        "request":{
            "method":"get",
            "url":"?type=one-string"
        },
        "response":{
            "code": 200,
             "name":"jsoncheck"
        }
    },{
        "name":"oneSting check type",
        "request":{
            "method":"get",
            "url":"?type=one-string"
        },
        "response":{
            "code": 200,
            "name":{"type":"string","value":"jsoncheck"}
        }
    }]
}
let request = new CR.Request('localhost:3008',{"authentication":"csadcas.cdcasd.cdac"})
request.request(data)
```

Check response number object

```js
//response
{
   code: 200,
   age: 20
}
const CR = require('check-rs-json')
let rules = {
    "name":"number-check",
    "data":[{
        "name":"number check",
        "request":{
            "method":"get",
            "url":"?type=one-number"
        },
        "response":{
            "code": 200,
             "age":20
        }
    },{
        "name":"oneSting check type",
        "request":{
            "method":"get",
            "url":"?type=one-number"
        },
        "response":{
            "code": 200,
            "age":{"type":"number","value":20}
        }
    }]
}
let request = new CR.Request('localhost:3008',{"authentication":"csadcas.cdcasd.cdac"})
request.request(data)
```

Check with two type object and subobject

```js
//response
 {
   code: 200,
   info: { name: "jsoncheck", age: 20 }
 }


const CR = require('check-rs-json')
let rules = {
    "name":"objectCheck",
    "data":[{
        "name":"object check",
        "request":{
            "method":"get",
            "url":"?type=two-object"
        },
        "response":{
            "code": 200,
             "info":{
                "type": "object",
                "children": {
                    "name":"jsoncheck",
                    "age":{"type":"number","value":20}
                }
             }
        }
    }]
}
let request = new CR.Request('localhost:3008',{"authentication":"csadcas.cdcasd.cdac"})
request.request(data)
```

Check with Array

```js
//response
{
   code: 200,
   info: [{ name: "jsoncheck", age: 20 },{ name: "tim", age: 21 }]
}


const CR = require('check-rs-json')
let rules = {
    "name":"arrayCheck",
    "data":[{
        "name":"array check",
        "request":{
            "method":"get",
            "url":"?type=array"
        },
        "response":{
            "code": 200,
             "info":{
                "type": "array",
                "children": [{
                    "name":"jsoncheck",
                    "age":{"type":"number","value":20}
                },{
                    "name":"tim",
                    "age":{"type":"number","value":21}
                }]
             }
        }
    }]
}

let request = new CR.Request('localhost:3008',{"authentication":"234567cdsc.cdcasd.csdacasd"})
request.request(data)
```

### POST

```js
//response
{
    code: 200,
    name: "jsoncheck"
}
const CR = require('check-rs-json')
let rules =  {
    "name":"oneSting",
    "data":[{
        "name":"oneSting check value",
        "request":{
            "method":"post",
            "url":"?type=one-string",
            "data":{"user":"tim","password":"1111111"}
        },
        "response":{
            "code": 200,
             "name":"jsoncheck"
        }
    }]
}
let request = new CR.Request('localhost:3008',{"authentication":"csadcas.cdcasd.cdac"})
request.request(data)
```

### Notes

The type check base on [chai.expect](https://github.com/chaijs/chai)
