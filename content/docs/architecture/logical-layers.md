---
uid: eisk-webapi-logical-layers
---
# Logical Layers

### Data Service Layer
 * Contains logic for accessing relational database.
 * Contains logic for invalidating cache memory.

### Domain Service Layer
 * Responsible for performing transformation from api data model to persistence data model and vice versa.     
 * Contains validation logic (typically that requires accessing relational and cached data) for api model and domain objects.
 * Performs other domain related services such as calculations, key generation etc
 * Depends on Data Access Layer

### API Controller
 * Serves as a http end point that resides between external consumers (such as admin web) and service layer.
 * Provides field level validation on api data model object
 * Accessible via HTTP Basic authentication
 * Depends on Service Layer 

### API Client
 * Provides a mechanism to access restful api as exposed by API Controller.
 * Provides the security mechanism to access secured services as exposed by API Controllers.
 * Depends on API Controller (via Restful interface) 

![alt tag](~/art/layers-architecture.png)    

