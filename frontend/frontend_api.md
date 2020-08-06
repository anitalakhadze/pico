# Pico Frontend API

## Synopsis

This document specifies the API routines for any frontend for Pico. The frontend uses REST API. 

## General Guide

Read [Rest API guide](https://www.restapitutorial.com/lessons/restquicktips.html).  This API fully conforms with the above mentioned guide. 

## General Model

For the purposes of our project, the model of the User consists of the following properties: 
 * id (number)
 * username (string)
 * password (string)
 * firstName (string)
 * lastName (string)
 * token (string)

## Specific Examples

**POST** /users/authenticate:
> Authenticate the user by finding his/her username and password in the database. If not found, return error. 


