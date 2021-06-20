## AiSight Study case :
This is a basic web application which interacts with Mercedes Connected Vehicle Experimental API.

### Manual setup 
1. Create a new directory and change to it 
> ` mkdir project && cd project `
2. Clone this repo to your current directory
> ` git clone https://github.com/HananeOB/AiSightProject.git `
3. Install required packages
> ` npm install `
4. The application uses a mongodb database, you need to have mongodb installed an running on your machine, you also need to update mongodb uri in the server program [line 17] if it is not the same.
5. Launch the server 
> ` node server.js `
6. The user interface is not hosted on a server, you can access it by opening index.html file in your browser.
The interface asks for a vehicle_id, you will need to use this one : 1234567890ABCD1234.
7. You can also send crud requests to the server, for instance :

* Get doors state
> ` curl -X GET http://localhost:8000/1234567890ABCD1234/doors/ `
* Get tires state 
> ` curl -X GET http://localhost:8000/1234567890ABCD1234/tires/ `
* Get the last 30 values of fuel level [the time differece between each value is a minute]
> ` curl -X GET http://localhost:8000/1234567890ABCD1234/fuel/30 `
* Lock all the doors of the vehicle :
```
  curl -X POST \
  http://localhost:8000/1234567890ABCD1234/doors/change \
  -H 'content-type: application/json' \
  -d '{ "command": "UNLOCK"}'
```