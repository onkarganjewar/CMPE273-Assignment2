# CMPE273-Assignment2
# Simple location & trip planner service in Go

This location service has various REST endpoints to store & retrieve locations. All the CRUD operations are performed and MongoDB has been used for data persistence.

## Features   

•	Create a new location:  POST   /locations    
•	Retrieve a stored location: GET  /locations/{location_id}    
•	Update an existing location: PUT /locations/{location_id}   
•	Delete a location: DELETE /locations/{location_id}   

Note: Location ids are nothing but the ObjectId (unique identifier of type BSON generated by MongoDB)   


## Requirements  
•	Golang latest stable version (I have used go1.5 on Windows)   
•	You can check the official golang releases here: https://golang.org/doc/devel/release.html  
• MongoDB deployment

## Installation

### Installing Go (In case if you don't have it)
•	There are various ways to install go according to the operating system that you’re working on.   
•	All the required files and step-by-step instructions can be found here : https://golang.org/doc/install    

### Installing Packages
After you have installed the Golang then run the following command      
```
go get github.com/onkarganjewar/CMPE273-Assignment2
```

You will also need to install the httprouter package which can be found here  
```
go get github.com/julienschmidt/httprouter
```

Installing the driver to connect to the MongoDB from Go
```
go get gopkg.in/mgo.v2
go get gopkg.in/mgo.v2/bson
```


### Deploying MongoDB

• All the instructions and relevant files for installing MongoDB can be found here  

 https://docs.mongodb.org/manual/installation/  
 

• You will also need to create a collection and connect to that MongoDB deployment using a standard connection URI like this
 
 ```
 mongodb://<dbuser>:<dbpassword>@ds012345.mongolab.com:12345/<dbname>
 ```
 
 Note : For security reasons, I have not disclosed the connection URI to my database

## Usage

Go to your workspace where the application is stored and start the application

```
go run tripplanner.go
```

While the connection is running open the REST Console and do any of the following CRUD operations like

####POST - To create a new location

##### Request 

```prolog
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

####Response

```
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


####GET - To retrieve a stored location

##### Request 

```prolog
GET /locations/564e7f130a956e266887fc85
```

####Response

```
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


####PUT - To update an existing location

##### Request 

```prolog
PUT /locations/564e7f130a956e266887fc85
```

####Response

```
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

####DELETE - To delete a location

##### Request 

```prolog
DELETE /locations/564e7f130a956e266887fc85
```

####Response

```
HTTP Response Code: 200
```
