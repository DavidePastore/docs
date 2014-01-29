---
title: API Reference

language_tabs:
  - shell: cURL
  - objective_c: iOS

toc_footers:
 - <a href='#'></a>
 - <a href='http://github.com/tripit/slate'>Powered by Slate</a>
---

# Introduction

BaasBox is a complete solution to implement the back end of your applications.

You can access all section using the sidebar on the left. The
documentation explains:

*  the BaasBox features (server side)
   * how to install BaasBox
   *  how to use admin console and has a detailed section about the REST
      API that you can use
   *  REST API

*  the SDK features

   *  iOS SDK

For a complete list of changes and new features, see the [changelog](http://www.baasbox.com/baasbox-server-0-7-2-released)

The Getting Started section will allow you to have rapidly a first
result of what BaasBox can give you. Enjoy!

# Installation

**System Requirements**  [Java VM 6](http://java.com/en/download/) or above. BaasBox is compiled with
Java 1.6.

1. Download the latest version from [here](http://www.baasbox.com/download/), keep
   in mind that until the 1.0 version will be released, BaasBox is not
   production-ready and therefore subject to change. For Windows
   Platforms on the same page you will find the `start.tar.gz` file.
2. Unzip the `baasbox-x.x.zip` file wherever you want.
3. Only for Windows Platforms: unzip the `start.tar.gz` file and put the
   extracted start.bat in the same directory
4. Type:
   * `start.bat` (on Windows)
   * `./start` (on *nix) You might need to grant execution permissions via
   `chmod +x ./start`

BaasBox will start it will listen on port 9000. Visit [http://localhost:9000/](http://localhost:9000/)
with your preferred browser. If everything worked fine, the BaasBox logo
should appear. Now you can open the administrator console: [http://localhost:9000/console](http://localhost:9000/console )
For further details about the console, you can read [console](#console).
That’s all! BaasBox is ready to go and to serve your apps! To stop the server just halt (Ctrl-C) the shell script.


# General Overview

BaasBox is a server that makes available a set of functions for the
backend of mobile applications. All you need is a **Java Virtual Machine
1.6 or higher**. BaasBox already has everything you need
for it to work: an application server and a DB server. 
BaasBox was born to be simple to use and manage. To migrate a BaasBox instance from a
server to another, you just have to zip the database folder and copy it
in the server target folder. Moreover, it is ready to use without
changing the configuration parameters. You just have to
launch the command ``./start`` (or ``start.bat`` on Windows) and BaasBox will
run. Should you need it, you can apply customize configuration parameters. See the [hacking section](#hacking).

## Available Functions

Available functions are:

-  Administration console:

   -  A convenient web based administration console is provided, through
      which the administrator can manage several aspects of BaasBox

-  Content management:

   -  Definition of "objects collection (AKA documents)"
   -  Creation, modification and deletion of objects
   -  Granting and revoking reading/modification/cancellation
      authorization on single objects
   -  Queries that allow specifying selection and
      ordering criteria
   -  Management of "special" contents called Assets, which may be files of any kind, 
      to which you can associate arbitrary JSON data

-  Users management:

   -  Signup, Login, Logout, profiles management (private, public
      features and so on), forgotten password recovery, link and log-in
      through Facebook and Google+
   -  Roles management: administrators, registered users, back-office
      users, creation of new roles.

-  Push notifications:

   -  Push notifications for iOS and Android devices

-  DB management:

   -  Backup/restore and reset of the integrated database
   

## Applied Technology

BaasBox is written mostly in Java, with some code in [Scala](http://www.scala-lang.org/). It uses the [Play! framework](http://www.playframework.com/) and it incorporates the core of the [OrientDB database](http://www.orientechnologies.com/orientdb/). This will allow BaasBox to natively manage the relations between JSON objects and to link
objects and queries without using specific abstractions or having to simulate them on the applicative level. OrientDB was recently surveyed and entered Gartner's Magic Quadrant.


# Console

BaasBox has a web console that allows managing its behavior and performing administrative
tasks. The console is a responsive one-page web application that
performs REST calls to the BaasBox admin APIs. This guide will
illustrate the console for the version **0.7.2**  We suppose that
BaasBox is deployed on localhost with its default parameters. If you
deployed BaasBox in the correct way, you can open your browser and open
the welcome screen: ![Console image](images/Console_0.7.2/home_console.png)

## Login screen

When you are in the start view, the administrator console is reachable
at the /console path. 
![Login image](images/Console_0.7.2/login.png)
To login in the administrative area you must supply the administrator credentials and the Application Code.
By default these values are:

-  Username: admin
-  Password: admin
-  App Code: 1234567890

You can change these values at any time by follow the instructions shown
in the [hacking section](#hacking). By clicking on the question marks, the
fields will be filled with the default values. 

## Dashboard 

Once you logged in, you will see the main dashboard screen: 

![Dashboard image](images/Console_0.7.2/baasbox_0-7-2-console.png)

The web console is based on twitter bootstrap and on the [Charisma Template](https://github.com/usmanhalalit/charisma/) project. The
dashboard is split into several sections:

1.  BaasBox version number
2.  Quick link to the BaasBox site
3.  Main menu to access all the main sections of BaasBox
4.  A trace of where you are located
5.  Number of users and rapid access to the relative section
6.  Number of documents (objects) stored in the embedded database and
    rapid access to the relative section
7.  Quick link to the [download](http://www.baasbox.com/download/) of BaasBox site where you
    can find the latest version
8.  Number of collections, documents and total size in one window.
9.  Here you can see all latest news about BaasBox. These are feeds from
    the BaasBox site |News|
10. System window:

    -  Memory: you can find max allocable memory, current allocated
       memory and current used memory
    -  OS: you can find name, version, architecture and processors
       viewed by your OS
    -  Java: you can find version, vendor and class version of your JDK
    -  Database: you can find version with its path and data size

11. Access to a dialog window to change password or to logout

    -  Change password: Just insert old and new passwords, then confirm
       the new one
    -  Logout: just logout from the console. Remember that you can also
       logout from the left menu.

12. Feedback tab: from there you can send us a feedback about your
    experience with BaasBox
13. DB Management: you can create backup of your DB and import & export
14. Roles: you can view and create roles for users

NOTE: you can hide all tables/sections that have the up-arrow button on
the right.


## Settings


By selecting the Settings option in the left menu you can access the
settings section. You can choose settings for applications, password
recovery, images and push notifications. Each record has the Edit button
that allows you to modify its action.

NOTE: the starred fields are mandatory.

## Database Management

The item **DB Management** allows you to perform some operations on the
database. 

![Dashboard image](images/Console_0.7.2/baasbox-db-management.png)

1. Restore a previously created backup file
2. Create a new backup
3. View the list of generated backups
4. Reinitialize the database at its initial state. It deletes all the
   database content.

To create a new backup, you have to click on the "Create a new
backup..." button. This operation is asynchronous. BaasBox will freeze
the database and it will stop responding to the clients. When the backup
is ready you will find it in the list. From that list you can download
it or delete it.

To restore a database you have to download a backup file locally, and
then use the restore feature.


## Users


By selecting the Users option on the menu you can access the users
section. 

![Users image](images/Console_0.7.2/users.png)


In this section you have the list of all users. A
single user has a name, a role (admin, anonymoususer, backofficeuser,
registereduser), a creation date, a status and actions. You also have a
search tool. If you want to create a new user, click on the New User
button and you will see this window:

![New user image](images/Console_0.7.2/create_new_user.png)

<aside class="notice">
Starred fields are mandatory. After you have filled at least the mandatory fields, 
you have to save the changes.
</aside>



## Collections

By selecting the Collections option on the menu you can access the
collection administration page. Collections are a sort of buckets where
you can store objects, also known as "documents". 

![Collections](images/Console_0.7.2/collections.png)

In this section you have a list of all your collections and you can quickly
find them with the search tool. To create a new collection, click on the
New Collection button and insert its name, then save the changes.

![New collection](images/Console_0.7.2/create_new_collection.png)


## Documents


Documents are objects stored in the embedded NoSQL database ad grouped
in "Collections".

![Documents](images/Console_0.7.2/documents.png)

In this section you have the list of all
your documents, but you have to select an existing collection at first.
In fact you can see all the documents relative to a specific collection.
Of course you also have the search tool. 

![Documents table](images/Console_0.7.2/baasbox-documents-table.png)

Each document has a unique id, generated by the server once it is stored.
Data documents are stored and retrieved JSON format.

Documents are accessible only by the user that created them. APIs exist
to grant and revoke permissions to the single users or roles.


## Assets


Assets are special objects. They are public by default, but only
administrators can create or delete them. They can store arbitrary data
(in JSON format), or entire files. Each Asset can store a file and its
associated data. Assets do not have IDs generated by the server, but you
can, indeed you MUST, assign a unique name to them. You can subsequently
use these names to reference the assets.

![Assets](images/Console_0.7.2/assets.png)

In this section you have the detailed list of all your assets
with information fields like Icon, Name, Meta, Size, Type, Download and
Actions. Of course you also have the search tool. If you want to create
a new asset, click on the New Asset button and you will see the
following window: 

![New asset](images/Console_0.7.2/new_asset.png)

<aside class="notice">
	You have to fill at least the Name
	field and save the changes to create a new asset.
</aside>









# REST API

## General Remarks

These are the general notes about the REST API protocol used by BaasBox
and its JSON format.

### Request Headers

If not specified otherwise, all requests need some custom HTTP headers.
BaasBox, since the 0.57 version supports two authentication method: HTTP Basic Authentication, or via a
Session Token.

### Basic Authentication


It needs to provide the user’s credentials via the basic access authentication method. Username and
password must be combined into a string “username:password” and then
encoded using BASE64. The header must be in the form: 

``Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==``

If the authentication fails, the
server replies with BAD REQUEST http error (code 400)

**X-BAASBOX-APPCODE**  This is the application code, by default this
is: ``1234567890``

## Session Token


To use this authentication method, the client have to call
the [Login](#login) API. The Server will provide a token to use in the
subsequent calls. All tokens will be invalidated if the server is stopped. To pass the session
token to the server, use the following header: 

``X-BB-SESSION: 0000-1111-2222-3333`` 

## The JSON response 

> A sample of a JSON response

```json 
{	
  "result": "ok|ko",
  "http_code": (200|201|204),
  "data": {  }
}
```

> An example of JSON error

```json
{
	"result": "error",
	"bb_code": "",
	"message": "a message explaining the problem in plain English",
	"resource": "the REST API called",
	"method": "the HTTP method used",
	"request_header": { the headers received by the server },
	"API_version": "...the BaasBox API version..."
}
```

Every response generated by BaasBox as a result of a REST call is a JSON
object. In case of error, the data returned are more detailed and are useful to
understand why the request was rejected. 


## Custom Error Codes


These are custom error codes specific to BaasBox

-  40001: You are attempting to update a database object with older
   data. Version is not the same
-  40101: Authentication info not valid or not provided. HINT: is your
   session expired?
-  50301: Push settings are not properly configured. HINT: go to
   administration console and check the settings
-  50302: The server cannot resolve the host name. HINT: check your
   internet connection 


## Query Criteria


Some APIs allow to specify query criteria. Accepted parameters are:

-  **where**: set a filter criteria in a SQL-like fashion (i.e.: ``“color=’yellow’ or address.city=’rome’”``). It is possible to use the positional mode, for example: ``“color=? or address.city=?”``. In this case you must supply the parameters’ values using the ``params`` querystring parameter.
-  **params**: an array of value for the where clause. For example:
   ``/API\_URL/WHERECLAUSE/&params=yellow&params=cyan``
-  **orderBy**: set an order by clause in a SQL-like fashion (i.e.:
   orderBy name desc). NOTE: the direction of ordering (asc or desc) is
   mandatory if pagination is used (see below)
-  **page**: a 0 based index indicating the page requested
-  **recordPerPage**: the number of records per page

**Example of valid calls**:

* ``/document/mycollection/count?where=color%3D’yellow’``
* ``/document/mycollection/count?where=color%3D%3F&params%3dyellow``
* ``/document/documents/count?where=color%3D%3F%20or%20color%3D%3F&params=yellow&params=cyan``

<aside class="notice">
	The value of the parameter must be URL encoded.
</aside>


## Sign up

> Sample request to create a user

```shell
curl http://localhost:9000/user \
	-d '{"username" : "cesare", "password" : "password"}' \
	-H Content-type:application/json \
	-H X-BAASBOX-APPCODE:1234567890  
```

```objective_c
BAAClient *client = [BAAClient sharedClient];
[client createUserWithUsername:@"cesare"
                      password:@"password"
                    completion:^(BOOL success, NSError *error) {

                          if (success) {
                              NSLog(@"user is %@", client.currentUser);
                          } else {
                              // display error
                          }

 }];
```

```java
EXAMPLE OF SIGNUP IN JAVA
```

> Sample response when a user is created

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-23 23:00:18",
    "X-BB-SESSION": "db7634df-1002-45a2-b2ab-0f6b8556a1fe"
  },
  "http_code": 201
}
```

``POST /user``

**Headers**: See authorization header in the [General Remarks](#general-remarks)

**Description**: This API allows a user to sign up to the App. Users will belong to the registered user role and
they will post new content, will retrieve their own content, will change their password. 

Parameter | Description
--------- | -----------
**username** | The username for the user. Mandatory
**password** | Password. Mandatory
**visibleByTheUser** | an object whose fields are private and  visible only by the user
**visibleByFriends** | an object whose fields are visible by the user and his/her friends (for future friendship management)
**visibleByRegisteredUsers** | is an object whose fields are visible by the user, his/her friends, any registered user
**visibleByAnonymousUsers** | an object whose fields are public and visible by everyone, even anonymous users



## Login

> Sample request to login 

```shell
curl http://localhost:9000/login \
	-d "username=cesare" \
	-d "password=password" \
	-d "appcode=1234567890"
```

```objective_c
BAAClient *client = [BAAClient sharedClient];
[client authenticateUser:@"user"
                password:@"password"
              completion:^(BOOL success, NSError *error) {
                  
			if (success) {
				NSLog(@"user is %@", client.currentUser);
			} else {
				// show error
			}
}];
```

> Sample response when a user is logged in

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-23 23:00:18",
    "X-BB-SESSION": "41b7ce0f-be44-4737-b346-907483155ad8"
  },
  "http_code": 200
}
```

``POST /login``

Checks username/password and grants the user the right to execute other calls. 
This API returns a session token (**X-BB-SESSION**) that must be provided into 
all authenticated calls.

Parameter | Description
--------- | -----------
**username** | The username for the user. Mandatory
**password** | Password. Mandatory
**appcode** | The appcode of your server instance


## Logout

> Example of logout call

```shell
curl -X POST http://localhost:9000/logout \
	-H X-BB-SESSION:da506029-4512-45a9-9606-43fcdda4121a
```

```objective_c
[BAAUser logoutWithCompletion:^(BOOL success, NSError *error) {
           
	if (success) {
	    // user logged out
	} else {
	    // error logging out
	}
            
}];
```

> Sample response when a user logs out

```json
{
 "result":"ok",
 "data":"user logged out",
 "http_code":200
}
```

``POST /logout/:deviceId`` 

Allows a user to logout from the app on a specific device. Push notification will not be sent to the user through the specified device.

Parameter | Description
--------- | -----------
**deviceId** | Optional. The id of the device on which you have activate push notifications.


## Logged user profile

> Request to fetch user profile currently logged in

```shell
curl http://localhost:9000/me \
	-H X-BB-SESSION:196f48ed-6154-4b49-8dc6-8b9b2ce4900a
```

```objective_c
[BAAUser loadCurrentUserWithCompletion:^(BAAUser *user, NSError *error) {
    
	if (error == nil) {
		// deal with user object
	} else {
		// deal with error
	}
		
}];
``` 

> Sample response 

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-24T11:28:09.009+0100"
  },
  "http_code": 200
}
```

``GET /me``

Retrieves details about the logged in user.







## Update user profile

> PUT request to update the logged in user profile

```shell
curl -X PUT http://localhost:9000/me \
	-d '{"visibleByFriends" : {"phoneNumber" : "+1123456"}}' \
	-H Content-type:application/json \
	-H X-BB-SESSION:a30e8f43-4d90-4324-91d2-6065fa6ca63c
```

```objective_c
TO BE IMPLEMENTED
```



> Sample JSON response

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-24T11:28:09.009+0100",
    "visibleByFriends": {
      "phoneNumber": "+1123456"
    }
  },
  "http_code": 200
}
```

``PUT /me``

Updates details about the logged in user.

The body payload to send has the following form:

```{
    "visibleByTheUser": {},
    "visibleByFriend": {},
    "visibleByRegisteredUsers": {},
    "visibleByAnonymousUsers": {}
}```

All the four properties are optional. You can send just
one of them or all four. See example on the right.
The values for this fields can be anything you like: string, numbers, arrays
or JSON encoded objects.

Parameter | Description
--------- | -----------
**visibleByTheUser** | fields private and visible only by the user
**visibleByFriend** | fields are visible by the user and his friends
**visibleByRegisteredUsers** | fields are visible by the user, his friends and any registered user
**visibleByAnonymousUsers** | fields are public and visible by everyone, even anonymous users

<aside class="warning">
	The previously stored content for each of the four fields will be overwritten.
</aside>






## Change password

> Example of request

```shell
curl -X PUT http://localhost:9000/me/password \
	-d '{"old" : "password", "new" : "newpassword"}' \
	-H Content-type:application/json \
	-H X-BB-SESSION:a30e8f43-4d90-4324-91d2-6065fa6ca63c
```

```objective_c
TO BE IMPLEMENTED
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

``PUT /me/password`` 

To change the password of the logged in user.

Parameter | Description
--------- | -----------
**old** | The old password. Mandatory.
**new** | The new password. Mandatory.

<aside class="warning">
	After you call this API the authentication token is not valid anymore and should should call [Login](#login) again.
</aside>









## Follow a user

> Example of request to follow the user "cesare"

```shell
curl -X POST http://localhost:9000/follow/cesare \
	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ...; // Instance of user to be followed

[BAAUser followUser:user
         completion:^(BAAUser *user, NSError *error) {
             
             if (error == nil) {
                 NSLog(@"now following user %@", user);                 
             } else {
                 // deal with error             
             }
                          
         }];
```

> Example response

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "roles": [
        {
          "name": "registered"
        },
        {
          "name": "friends_of_cesare"
        }
      ],
      "status": "ACTIVE"
    },
    "signUpDate": "2014-01-24T11:28:09.009+0100",
    "visibleByFriends": {
      "phoneNumber": "+1123456"
    }
  },
  "http_code": 201
}
```

``POST /follow/:username``

This API allows a user to follow another user. Once the relation is established
the follower will be able to see the documents and files created by the followed 
user as well as its `visibleByFriends` data in the user profile.

Parameter | Description
--------- | -----------
**username** | Username of the user to be followed. Mandatory.








## Unfollow a user

> Example of unfollow request

```shell
curl -X DELETE http://localhost:9000/follow/cesare \
 	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ...; // Instance of user to be unfollowed

[BAAUser unfollowUser:user
           completion:^(BAAUser *user, NSError *error) {
             
	             if (error == nil) {
	                 NSLog(@"not following anymore user %@", user);                 
	             } else {
	                 // deal with error             
	             }
                          
         }];
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

``DELETE /follow/:username``

This API allows a user to unfollow another user. Once the relation has been deleted, the user 
won't be able anymore to see documents and files created by the unfollowed user.

Parameter | Description
--------- | -----------
**username** | Username of the user to be unfollowed. Mandatory.







## Fetch following

> Example of request to fetch who "cesare" is following

```shell
curl http://localhost:9000/following/cesare \
 	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ... // user representing "cesare"

[user loadFollowingWithCompletion:^(NSArray *following, NSError *error) {
                        
            for (BAAUser *u in following) {
                NSLog("cesare is following %@", u)
            }
            
        }];
```

> Example of response

```json
{
  "result": "ok",
  "data": [
    {
      "user": {
        "roles": [
          {
            "name": "registered"
          }
        ],
        "name": "a",
        "status": "ACTIVE"
      },
      "signUpDate": "2014-01-24T12:13:08.008+0100"
    }
  ],
  "http_code": 200
}
```

``GET /following/:username``

This API returns a list of users that are followed by the user with `username` passed as parameter. The method returns in its `data` property an array filled with the user profiles representing its “friends”. Each profile will contain the `visibleByFriends` data which would be otherwise hidden.

Parameter | Description
--------- | -----------
**username** | Username of the user whose following list has to be fetched. Mandatory.








## Fetch followers

> Example of request to fetch who "cesare"'s followers

```shell
curl http://localhost:9000/followers/cesare \
	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ... // user representing "cesare"

[user loadFollowersWithCompletion:^(NSArray *following, NSError *error) {
                        
            for (BAAUser *u in following) {
                NSLog("%@ is following cesare", u)
            }
            
        }];
```

> Example of response with "cesare"'s followers


```json
{
  "result": "ok",
  "data": [
    {
      "user": {
        "roles": [
          {
            "name": "registered"
          }
        ],
        "name": "a",
        "status": "ACTIVE"
      },
      "signUpDate": "2014-01-24T12:13:08.008+0100"
    }
  ],
  "http_code": 200
}
```

``GET /followers/:username``

This API returns the list of followers for the user with `username` specified in the parameter. The method returns in its `data` property an array filled with the user profiles representing its “friends”. Each profile will contain the `visibleByFriends` data which would be otherwise protected. 

Parameter | Description
--------- | -----------
**username** | Username of the user whose followers list has to be fetched. Mandatory.



## Password reset

> Example of request for password reset

```shell
curl http://localhost:9000/user/cesare/password/reset \
	-H X-BAASBOX-APPCODE:1234567890
```

```objective_c
TO BE IMPLEMENTED
```

> Example of error

```json
{
  "result": "error",
  "message": "Cannot reset password, the \"email\" attribute is not defined into the user's private profile",
  "resource": "/user/cesare/password/reset",
  "method": "GET",
  "request_header": {
    "Accept": [
      "*/*"
    ],
    "Host": [
      "localhost:9000"
    ],
    "X-BAASBOX-APPCODE": [
      "1234567890"
    ]
  },
  "API_version": "0.7.3-snapshot"
}
```


``GET /user/:username/password/reset``

Allows to reset a user password. This API is useful when a user forgot their password and needs to reset it. This is the workflow: 

- the server checks if the email address is present within the `visibleByTheUser` fields in the user profile 
- the server sends an email to that address with a generated link to follow to reset the password 
- the user opens the email and opens the given link in a web browser. That shows a form with two html password fields. 
- The user fills in the two fields and submits the form 
- A confirmation message is shown by the server 
- The settings (SMTP configuration, email message to be sent, html form, confirmation and error web page) can be setup by the administrator via the [Settings](#settings) menu in the admin console.

Parameter | Description
--------- | -----------
**username** | Username of the user who wants to reset the password. Mandatory.

<aside class="warning">
This API works only if there is an `email` field (populated with a valid email address) in the `visibleByTheUser` field of the user profile
</aside>



# Hacking