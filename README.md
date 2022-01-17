#API GATEWAY
.net Core 5.0 


Dependency: 

Ocelot

consul

Consul is going to provide loadbalancer in our project.
To run it via docker :
docker pull consul
docker run -p 8500:8500 consul



API gateway sample base project. 

Depends on related repositories :

ProfileService   ==>  working on port 9980
EducationService   ==>  working on port 9981
SuggestionService  ==> working on port 9982




API Gateway forwards requests to mapped route defined in ocelot.json


Following expression means  incoming request to route "/myawesomeapi/user/{id}"  will be forwarded  to endpoint  "/api/platformuser/{id}" working on port 9980 

 {
    <b style="color:green">      "UpstreamPathTemplate": "/myawesomeapi/user/{id}",</b>
      "UpstreamHttpMethod": [
        "Get"
      ],
   <b style="color:green">       "DownstreamPathTemplate": "/api/platformuser/{id}",</b>
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
         <b style="color:green">    "Port": 9980 </b>
        }
      ],
      "Key": "User"
    },


