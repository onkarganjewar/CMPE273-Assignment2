# RESTful Location & Trip planner Service in Golang

This RESTful Web Service has several endpoints to store & retrieve locations. Implemented all the CRUD operations, used MongoDB for data persistence.

## Features   

* Create a new location  

```http
POST   /locations
```

* Retrieve a stored location 

```http
GET  /locations/{location_id}    
```

* Update an existing location 

```http
PUT /locations/{location_id}   
```

* Delete a location 

```http
DELETE /locations/{location_id}   
```


```Shell
Note: Location ids are nothing but the ObjectId (unique identifier of type BSON generated by MongoDB)   
```


## Requirements  
*	[Golang](https://golang.org/dl/) (I have used go1.5 on Windows)   
* [MongoDB](https://www.mongodb.com/)


## Installation

### Installing Go 
*	If you don't have it configured on your OS, check out [this official manual](https://golang.org/doc/install) for the step-by-step instructions to install Go.   

### Installing Packages

1. Install this repository/package using Go      
```Shell
go get github.com/onkarganjewar/CMPE273-Assignment2
```

2. Install the httprouter package  
```Shell
go get github.com/julienschmidt/httprouter
```

3. Install the MongoDB driver for Go
```Shell
go get gopkg.in/mgo.v2
go get gopkg.in/mgo.v2/bson
```


### Deploying MongoDB

• All the instructions for installing MongoDB can be found [here.](https://docs.mongodb.org/manual/installation/)  

• You will also need to create a collection, and connect to that MongoDB deployment using a standard connection URI like this:
 
 ```Shell
 mongodb://<dbuser>:<dbpassword>@ds012345.mongolab.com:12345/<dbname>
 ```
 
## Demo

* Change directory to your workspace and start the server

 ```Shell
 go run tripplanner.go
 ```

* Application will now run at http://localhost:3022/

* Use any [REST client console](https://chrome.google.com/webstore/detail/rest-console/cokgbflfommojglbmbpenpphppikmonn) or [POSTMAN](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en) chrome extensions to test the following endpoints:


### POST - Create a new location

#### Request 

```http
POST /locations
```

```json
{
   "name" : "Bob Smith",
   "address" : "123 Main St",
   "city" : "San Jose",
   "state" : "CA",
   "zip" : "95112"
}
```

#### Response

```http
HTTP Response Code: 201
```

```json
{
    "id": "564e7f130a956e266887fc85",
    "name": "Bob Smith",
    "address": "123 main street",
    "city": "San Jose",
    "state": "CA",
    "zip": "95112",
    "coordinate": {
        "lat": 37.128988,
        "lng": -121.656946
    }
}
```


### GET - Retrieve a stored location

#### Request 

```http
GET /locations/564e7f130a956e266887fc85
```

#### Response

```http
HTTP Response Code: 200
```

```json
{
    "id": "564e7f130a956e266887fc85",
    "name": "Bob Smith",
    "address": "123 main street",
    "city": "San Jose",
    "state": "CA",
    "zip": "95112",
    "coordinate": {
        "lat": 37.128988,
        "lng": -121.656946
    }
}
```


### PUT - Update an existing location

#### Request 

```http
PUT /locations/564e7f130a956e266887fc85
```

#### Response

```http
HTTP Response Code: 202
```

```json
{
    "id": "564e7f130a956e266887fc85",
     "name" : "John Smith",
   "address" : "1600 Amphitheatre Parkway",
   "city" : "Mountain View",
   "state" : "CA",
   "zip" : "94043",
   "coordinate" : { 
      "lat" : 37.4220352,
     "lng" : -122.0841244
   }
}
```

### DELETE - Delete a location

#### Request 

```http
DELETE /locations/564e7f130a956e266887fc85
```

#### Response

```http
HTTP Response Code: 200
```
