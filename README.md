##Project 4

## Getting started

```
npm install
```

## Testing

```
npm test
```

## Endpoint description

### 1. Blockchain ID validation request

**Example**

````bash
$ curl -X "POST" "http://localhost:8000/requestValidation" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "address": "sample address from project 1"
}'
````

`Response`
````json
{
  "address":"address",
  "message":"adress+message",
  "requestTimeStamp":1541158973868,
  "validationWindow":300
}
````

### 2. Blockchain ID message signature validation

**Example**

````bash
$ curl -X "POST" "http://localhost:8000/message-signature/validate" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "address": "sampleadress",
  "signature": "signaturefrom your wallet or by code"
}'
````

`Response`

````json
{
  "registerStar":true,
  "status": {
    "address":"14TwaGf3yy8F2E99f2kWmU34n2PmdrV7tR",
    "message":"14TwaGf3yy8F2E99f2kWmU34n2PmdrV7tR:1541159974311:starRegistry",
    "requestTimeStamp":1541159974311,
    "validationWindow":211,
    "messageSignature":"valid"
  }
}
````

### 3. Star registration

**Example**
````bash
$ curl -X "POST" "http://localhost:8000/block" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "address": "14TwaGf3yy8F2E99f2kWmU34n2PmdrV7tR",
  "star": {
    "dec": "-26° 29'\'' 24.9",
    "ra": "16h 29m 1.0s",
    "story": "Found star using https://www.google.com/sky/"
  }
}'
````
`Response`
````json
{
  "hash": "56bc82e0380d465d2931f2d3ed2f02eab7db607993e064eaf2c495d65094f282",
  "height": 1,
  "body": {
    "address": "14TwaGf3yy8F2E99f2kWmU34n2PmdrV7tR",
    "star": { 
      "dec": "-26° 29' 24.9",
      "ra": "16h 29m 1.0s",
      "story": "466f756e642073746172207573696e672068747470733a2f2f7777772e676f6f676c652e636f6d2f736b792f"
    }
  },
  "time":"1541160381",
  "previousBlockHash":"9fd57f8eff4cd0520887b458330f4c2ef6e7f33864942d40fc1c76918e0f0b0f"
}
````                        

### 4. Get block by height



```bash
$ curl "GET" "http://localhost:8000/block/0"
```

`Response`
```json
{"hash":"6e04b1611aeb9d0b880485cba2e1e09a93052fe3f66e1e61a02d52520ff301ae",
"height":0,
"body":"Genesis block",
"time":"1546974093",
"previousBlockHash":""}
```

### 5. Get block by address

**Example**

````bash
$ curl "http://localhost:8000/stars/"sampleaddress"
````
```json
[
  {
    "hash": "56bc82e0380d465d2931f2d3ed2f02eab7db607993e064eaf2c495d65094f282",
    "height": 1,
    "body": { 
      "star": {
        "dec": "-26° 29' 24.9",
        "ra": "16h 29m 1.0s",
        "story": "466f756e642073746172207573696e672068747470733a2f2f7777772e676f6f676c652e636f6d2f736b792f",
        "storyDecoded": "Found star using https://www.google.com/sky/",
      }
    },
    "time": "1541160381",
    "previousBlockHash": "9fd57f8eff4cd0520887b458330f4c2ef6e7f33864942d40fc1c76918e0f0b0f",
  }
]
```
