### About

Your web service will provide a few new features to your users. The goal is to allow users to notarize star ownership using their blockchain identity.


## Usage

### Installation

## Run App

```sh
git clone https://github.com/joseasousa/PrivateBlockchain.git
cd PrivateBlockchain
npm install
```

This installs the dependencies of the project.

### Start API server
```sh
npm start
```
This starts the API server, listening on port 8000 of localhost.

### Endpoints
The endpoints implemented are:

### 1. Blockchain ID validation request

## POST /requestValidation


Sample input:
```json
{
  "address": "String Test"
}
```
**Parameters**

```
address - A bitcoin address, you can take it from your project1
```

**Example**
```json
{
  "address": "142BDCeSGbXjWKaAnYXbMpZ6sbrSAo3DpZ"
}
```



### 2. Blockchain ID message signature validation

## POST /message-signature/validate

**Parameters**

```
address - The addres that you used in last step
signature - You can take it from the Electrum wallet (see below) or make it by code (see test/index.test.js)
```

**Example**

```json
{
  "address": "142BDCeSGbXjWKaAnYXbMpZ6sbrSAo3DpZ",
  "signature": "IJtpSFiOJrw/xYeucFxsHvIRFJ85YSGP8S1AEZxM4/obS3xr9iz7H0ffD7aM2vugrRaCi/zxaPtkflNzt5ykbc0="
}
```

### 3. Star registration

## POST /validate/block

**Parameters**

```
address - The addres that you used in last step
star - Containing dec, ra and story (max 500 bytes)
```

**Example**

```json
{
  "address": "142BDCeSGbXjWKaAnYXbMpZ6sbrSAo3DpZ",
  "star": {
        "ra": "16h 29m 1.0s",
        "dec": "-26° 29' 24.9",
        "story": "466f756e642073746172207573696e672068747470733a2f2f7777772e676f6f676c652e636f6d2f736b792f"
      }
}
```

### 4. Get block by height


## GET /block/:height


**Parameters**

```
height - The height of block
```

**Example**
```json
{
    "hash": "a59e9e399bc17c2db32a7a87379a8012f2c8e08dd661d7c0a6a4845d4f3ffb9f",
    "height": 1,
    "body": {
      "address": "142BDCeSGbXjWKaAnYXbMpZ6sbrSAo3DpZ",
      "star": {
        "ra": "16h 29m 1.0s",
        "dec": "-26° 29' 24.9",
        "story": "466f756e642073746172207573696e672068747470733a2f2f7777772e676f6f676c652e636f6d2f736b792f",
        "storyDecoded": "Found star using https://www.google.com/sky/"
      }
    },
    "time": "1532296234",
    "previousBlockHash": "49cce61ec3e6ae664514d5fa5722d86069cf981318fc303750ce66032d0acff3"
  }
```

### 5. Get block by hash


## GET /stars/hash:hash

**Parameters**

```
hash - The hash of one block created before
```

**Example**

<img src="">


### 6. Get block by address

## GET /stars/address:address


**Parameters**

```
address - The address used so far
```

**Example**

```json
{
    "hash": "a59e9e399bc17c2db32a7a87379a8012f2c8e08dd661d7c0a6a4845d4f3ffb9f",
    "height": 1,
    "body": {
      "address": "142BDCeSGbXjWKaAnYXbMpZ6sbrSAo3DpZ",
      "star": {
        "ra": "16h 29m 1.0s",
        "dec": "-26° 29' 24.9",
        "story": "466f756e642073746172207573696e672068747470733a2f2f7777772e676f6f676c652e636f6d2f736b792f",
        "storyDecoded": "Found star using https://www.google.com/sky/"
      }
    },
    "time": "1532296234",
    "previousBlockHash": "49cce61ec3e6ae664514d5fa5722d86069cf981318fc303750ce66032d0acff3"
  }
```