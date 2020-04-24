# **Group Project - README**
# Messaging-Hub

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
All in one messaging hub using API calls to WhatsApp, Facebook messenger, Instagram and Twitter to pull DMs to display them all in one application
### App Evaluation

- **Category:** Social Networking
- **Mobile:** All device types
- **Story:** Link to multiple accounts including WhatsApp facebook instagram and twitter and access chats
- **Market:** To all individuals who use multiple social apps
- **Habit:** Convient users who have multiple social app accounts and allow them to send and reply messages.
- **Scope:** First we would let users to login to the messaging-hub, and then the user can link the social app accounts

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

*  User logs in with the finger print 
*  User can link their social app accounts
*  User selects social account 
*  User can start the chat


### 2. Screen Archetypes

* Login Screen
   * login to Messaging-Hub
* Home Selection Screen
    * Select the social account 
* Message Screen
   * start the chat

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Login Screen
* Home selection Screen
* List of Messages Screen
* Messages Screen



## Wireframes

![](Messaging-Hub.gif)


### [BONUS] Digital Wireframes & Mockups

### [BONUS] Interactive Prototype

## Schema 
[This section will be completed in Unit 9]
### Models
Data Models:


 | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | author        | Pointer to User|  Name / profile image of author recipient |
   | object        | String   | Unique id for each message |
   | CreatedAt       | DateTime | Date / Time when a message is sent |
   | MessagesCount | Number   | Number of messages inside of a conversation|
   | objectId    | String   | Unique id for the user |







### Networking
#### List of network requests by screen
   - Home Message Screen
      - (Read/GET)  Query all chats where user is author
         ```swift
         let query = PFQuery(className:"Post")
         query.whereKey("author", equalTo: currentUser)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let posts = posts {
               print("Successfully retrieved \(posts.count) posts.")
           // TODO: Do something with posts...
            }
         }
         ```
      - (Delete) Delete existing chat
   - Chat Screen
      - (Read/Get) Query all the messages
      - (Create/POST) Send a new Message
   

   
      




 -Existing API Endpoints
> Receive Messages (GET direct_messages)

Resource URL: https://api.twitter.com/1.1/direct_messages/events/show.json

-> Send Messages (POST direct_messages)

Resource URL: 
https://api.twitter.com/1.1/direct_messages/events/new.json

-> Delete Messages (DELETE direct_messages/events/destroy)

Resource URL: https://api.twitter.com/1.1/direct_messages/events/destroy.json
 

