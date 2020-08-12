# Pico backend API

## Synopsis

This document specifies the API routines for any backends for pico. The backend uses  [REST API](https://www.restapitutorial.com/lessons/restquicktips.html)  to manage CRUD operations. The backend is supposed to be a thin wrapper around the underlying database system.  

## General guide

Read [Rest API guide](https://www.restapitutorial.com/lessons/restquicktips.html).  This API fully conforms with the above mentioned guide. For a concrete example, suppose you wish to find all "fruits" with respect to some parameter "ripeness", on the condition that "ripeness" is "good". Then the request should be  
> **GET** /fruits?ripeness=good  

To read data about "fruits" with unique identifier "apple" :
> **GET** /fruits/apple

To get the "weight" for that particular fruit:
> **GET** /fruits/apple/weight

The GET requests do not modify the data. However, if you wish to create a new "fruit", use:
> **POST** /fruits

With parameters to create the entry as a JSON object like this  
>{
>"name":"cherry",
>}

Pass GET parameters in *?param1=val1* format.  
Unless specified in a URL (ex. /users/:id) a parameter 'foo' must be sent as a Json.  
Every parameter name followed by a "?" question mark is optional.  
Unless specified otherwise, every request returns an appropriate HTTP response (ex. 200, 404, ...).
 [see tutorial](https://www.restapitutorial.com/lessons/httpmethods.html)

## Supported CRUD operations  
### Users  

#### Find particular user
> **GET** /users/:id

returns a user object, or empty object.

#### List users
> **GET** /users?{parameters}

returns an array of at most 10 matching user objects.

parameters:

- name?: string: name to filter users.

#### Save user
> **POST** /users

parameters:

- name: string: name of user (not username)

returns:

- id: unique identifier of a new user
- password: password of newly created user (save it!)

#### Update user

> **PATCH** /users/:id

parameters:

- id: unique identifier of existing user
- password: password of existing user
- ... any other modifiable user params

#### Delete user

> **DELETE** /users/:id  

parameters:  

- id: unique identifier of existing user
- password: password of existing user


