Leadwallet API Documentation
=============================

Note that URLs should be prefixed with **/api/v1/wallet**. For example, to create a wallet, URL should be in the form **/api/v1/wallet/:route** where *route* could be any of the following:

| Route | Method | Description                       | Parameters |
|-------|--------|-----------------------------------|------------|
|create | POST   |Generates a wallet.         |<table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>recoveryPhrase</td><td>body</td><td>An array of phrases from which to generate wallet's private key</td></tr></table>                        |
|retrieve| GET   |Returns a wallet using a key pair. |<table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>Authorization</td><td>headers</td><td>A bearer token that contains the key pair from which a private key would be gotten.</td></tr></table> |
|import  | POST  |Imports or recovers a wallet.      | <table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>recoveryPhrase</td><td>body</td><td>An array of phrases. A private key is generated from this and a wallet with a matching key is returned.</td></tr></table> |
|update  | GET   | Updates wallet details to reflect latest changes. | <table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>Authorization</td><td>headers</td><td>A bearer token that holds a payload containing a key pair</td></tr></table> |
|send_token | POST | Sends some token to another wallet.| <table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>type</td><td>body</td><td>The type of coin you're sending. Note that each type of coin also requires specific parameters to be sent in the body of the request. They'll be explained below.</td></tr><tr><td>Authorization</td><td>headers</td><td>A bearer token containing a payload. Would be used in determining the sender's address for some coins.</td></tr></table> | 


#### Parameters for different coin types
The following are the presently supported coin types:

**btc** - Bitcoin

**eth** - Ethereum

**doge** - Dogecoin

**dash** - Dashcoin

**tron** - Tron

**ltc** - Litecoin

For type **btc**, the following parameters should also be sent in the request body for the endpoint *send_token*

* **inputs**: An array of objects that contain an address and value key-value pair where address is the address from which you're sending coins and value is the amount you're sending.

```json
[
 {
  "address": "mjYuiio09ljkL",
  "value": 0.001
 }
]
```

* **outputs**: An array of objects that contain an address and value key-value pair where address is the address to which you're sending coins and value is the amount you're sending.

```json
[
 {
  "address": "mjYuiio09ljkL",
  "value": 0.001
 }
]
```

* **fee**: Fee that is incurred for sending BTCs.

```json
{
 "type": "btc",
 "fee": 0.0008,
 "inputs": [...],
 "outputs": [...]
}
```

For type **eth**

* **toAddress**: The address to which you're sending ETHs.

```json
{
 "toAddress": "0xghhsttsjskwo"
}
```

* **gasPrice**: ETH gas price.

```json
{
 "gasPrice": 489000998
}
```

* **gasLimit**: ETH gas limit.

```json
{
 "gasLimit": 21000
}
```

* **value**: The amount of ETHs you're sending.

```json
{
 "value": 0.1111278
}
```

* **passphrase**: A string of random phrases.

```json
{
 "passphrase": "Hearken Vehement Transcend Alibi Abet Circumvent Bare Ludicrous Anarchy"
}
```


For type **tron** 

* **to**: The address to which you're sending some TRONs.

```json
{
 "to": "HYgnummmldoiiop"
}
```

* **amount**: The amount of TRONs you're sending.

```json
{
 "amount": 200
}
```


For type **ltc**

LTC requires the same request body as BTC. The only exception is the *fee* field. For LTC, this field is an object that takes *value* as the only key.

```json
{
 "fee": {
  "value": 10
 }
}
```


For type **dash**

DASH requires the same request body as LTC.


For type **doge**

DOGE requires the same request body as LTC.
