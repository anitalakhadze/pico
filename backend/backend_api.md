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

Parameters for GET are always passed in with the URL, while for POST, parameters are always passed in with JSON object.

## Users

Find particular user
> **GET** /users/:id

returns a user object, or empty object.

List users
>**GET** /users?name=:name,regex=:regex

returns an array of at most 10 matching user objects.

parameters:

- id: string: unique identifier of a user.
- name: string: name of user.
- regex: boolean: use regex to find name.
