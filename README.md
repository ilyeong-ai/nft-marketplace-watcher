Vefi NFT Marketplace IPFS & API Doc
====================================


#### IPFS


For now, our IPFS is deployed at `http://20.118.216.88:7344`. This is the root URL before we get a domain. You can interact with the gateway using the following endpoints:

*Endpoint:* **`/ipfs/file`**

*Method:* **`POST`**

*Content Type:* **`multipart/form-data`**

*Description:* Pin a file to IPFS server

*Parameters:* 

  - file:
      * in: **`body`**
      * type: **`file`**

*Response:*

```json
{
  "response": {
    "fileURI": "http://...", // URI for image
    "CID": "Q..." // Image identifier
  }
}
```


*Endpoint:* **`/ipfs/json`**

*Method:* **`POST`**

*Content Type:* **`application/json`**

*Description:* Pin JSON metadata.

*Parameters:* Any JSON body is accepted. Use this endpoint to store metadata for collections/NFTs.

*Response:*

```json
{
  "response": {
    "itemURI": "http://...", // URI for item
    "CID": "Q..." // Item identifier
  }
}
```




#### API

The API for now, is deployed at `http://20.118.216.88:6008/`. Interact with the API using the following endpoints:


*Endpoint:* **`/api/account`**

*Method:* **`POST`**

*Content-Type:* **`application/json`**

*Parameters:*

  - accountId
    * in: `body`
    * type: `string`
    * description: `Address of account owner`
    * required: `true`
  - name
    * in: `body`
    * type: `string`
    * description: `Name of account owner`
    * required: `true`
  - email
    * in: `body`
    * type: `string`
    * description: `Email of account owner`
    * required: `true`
  - imageURI
    * in: `body`
    * type: `string`
    * description: `Image of account owner`
    * required: `false`
  
*Response:*

```json
{
  "result": {
    // User's info
    "token": "5..." // Json web token
  }
}
```


*Endpoint:* **`/api/account`**

*Method:* **`GET`**

*Description:* Retrieve account from request.

*Parameters:* 

  - Authorization
    * in: `header`
    * type: `string`
    * description: `Bearer token`
    * required: `true`

*Response:*

```json
{
  "result": {
    // Decoded user's info
  }
}
```


*Endpoint:* **`/api/collection/:network/all`**

*Method:* **`GET`**

*Description:* Fetch all collections by network. `:network` is path placeholder for network slug.

*Parameters:*

  - network
    * in: `path`
    * type: `string`
    * description: `Network slug`
    * required: `true`
