---
title: "API  101 : Introduction & Imp.(₿) of API Paradigms"
seoTitle: "API  101 : Introduction & Imp.(₿) of API Paradigms"
seoDescription: "All about APIs and the Power of Paradigms with real-world examples of companies like Twitter, GitHub, Slack, Stripe and a lot more."
datePublished: Wed Jun 28 2023 12:30:39 GMT+0000 (Coordinated Universal Time)
cuid: cljfp34cy000409mt6q4pftr1
slug: api-101-introduction-imp-of-api-paradigms
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687956889747/e4da4d76-7579-48b2-901f-5103cc5e9f81.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1687957001223/005ebb97-6233-48b9-b2fe-3ab8252f45c3.png
tags: technology, backend, apis, hashnode, wemakedevs

---

# Introduction

API which stands for Application Programming Interface is the most popular component of the modern-day application infrastructure which as according to the definition, APIs are the building blocks that allow interoperability for major business platforms on the web. APIs are the reason behind the creation and maintenance of identity across cloud software accounts.

APIs have emerged in order to exchange information with providers of data who are equipped to solve specific problems, so folks at other companies don't have to worry about solving those problems themselves.

For example, in the season of so many chatbots and AI models, developers who want to build another super intelligence or an AI tool integration of chatbots, don't have to build up a whole chatgpt by themselves. Someone who is starting up his/her own business out of any particular commodity or service doesn't have to build up a whole Google map only to mention and show up their office location on the street and city maps or to deliver the ordered products to their customer's address.

The creation of useless and weak APIs can eventually lead to a lot of money leakage from your pockets as changing from one API model to another type is highly expensive and exhausting for developers in any company, so it becomes really important for developers to prevent from building APIs that no one wants to use or which doesn't fit the usage requirements of your developers.

An API must be aligned with the core business as in the case of many Software as a Service (SaaS) companies. Consumer APIs also work well if there is a critical mass of user-generated content. There is also a clear reason not to create a developer platform when the API strategy is not aligned with the core business as in the case of Twitter.

API development is normally structured in mainly three different ways in most of companies:

## APIs for

### Internal Developers first then External

Companies could build potential value by adding an external API which could create a developer ecosystem, drive new demand for the company's product and build relations with big leaders and firms.

Slack is one of the companies that build their own API originally and then launched its Developer platform and a suite of products for third-party developers to build their own apps, both at established companies & new startups, and the advantage of this already established API was that when Slack's APIs were launched they are already well used, tested and planned by their own developers.

While the Disadvantage showed up when the needs of external developers drifted apart from the needs of internal developers, as the internal developers need flexibility for creating new features, resources, tools and experiences for the end users of messaging clients from the new type of shared channel, files, and other complex communication experiences. While Third-party developers have already started to create powerful business application displays.

### External Developers first then Internal

In this method, APIs are created for the external stakeholders first and then release to internal stakeholders.

The GitHub API audience was primarily external developers who wanted to gain programmatic access to their own data. GitHub has expanded and created an API that serves both individuals who want to create their own personal projects or workflows and team that want to collaborate to build bot scripts or workflow tools that integrate with GitHub.

One of the Advantages seen by GitHub is that API can be customized to serve external developers saving up a lot of time in straddling two audiences. Secondly, Github is able to annotate its JSON(JavaScript Object Syntex) responses with more and more data that developers needed.

Eventually, the Payloads were so large GitHub implemented GraphQL, helping developers specify the fields they wanted with the queries, but due to the creation of so many methods within the same file compromised the complexity of the files and make troubleshooting a lot tricker than before, which we will soon be discussing in this blog.

### API as the Product

Strip provides APIs for payment processing on the Internet. Twillio Provides APIs for communication via SMS, voice, and messaging. In the case of these two companies, building an API is 100% aligned with the single-product audience.

The API is the product, and the entire business aligns behind building a seamless interface for customers. As far as managing APIs and meeting user needs, the API as the product is the most straightforward company arrangement possible.

# API Paradigms

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687954304273/545bb4cd-bfee-48c2-b781-b9051fcebf00.jpeg align="center")

An API Paradigm defines the interface exposing the backend data of a service to other applications. There are different types of API Paradigms in general used by different organizations it isn't compulsory to use a single one out of all of them. many companies like Slack uses multiple Paradigms for different tasks and manage to build out a perfect infrastructure to deal with the pros and cons of every pattern.

**Request-Response API**

Request-Response API typically exposes an interface through an HTTP- based web server. API defines a set of endpoints. The client makes HTTP request to the server for the data to the endpoints and the server in return sends back responses written in the form of JSON and XML. There are three common paradigms used by services to expose request-response APIs: REST, RPC and GraphQL.

## Representaional Set Transfer(REST)

REST is one of the most popular paradigms used by the providers like Google, GitHub, Stripe and Twitter. REST works upon resources, which are entities that can be identified, held, named and addressed on the web. **REST uses HTTP methods to represent Create, Read, Update and Delete(CRUD)** transactions. REST APIs return JSON or XML responses, due to their simplicity and ease of use with JavaScript, JSON(JavaScript Object Syntex) has become the standard for modern API.

These Create, Read, Update and Delete(CRUD) transactions inform the server about the action to be performed. different HTTP methods invoked on the same URL provide different functionalities as:

**Create** Use POST for creating new resources.

**Read** Use GET for reading resources. They have no side effects: the GET method has a read-only semantic. GET is idempotent.

**Update** Use PUT for replacing a resource and PATCH for partial updates for existing resources.

**Delete** Use DELETE for deleting existing resources.

| OPERATION | HTTP verb | URL:/users | URL:/usersU123 |
| --- | --- | --- | --- |
| Create | POST | Create a new user | not applicable |
| Read | GET | List all the users | retrieve user U123 |
| Update | PUT or PATCH | Batch update users | Update user U123 |
| Delete | DELETE | Delete all users | Delete user U123 |

A resource that exists only within another resource can be better represented as a subresource instead of a top-level resource in the URL. this makes the relationship clear for the developers using the API.

**POST** `/repos/:owner/:repo/issues`

**GET** `/repos/:owner/:repo/issues/:number`

**GET** `/repos/:owner/:repo/issues`

**PATCH** `/repos/:owner/:repo/issues/:number`

## Remote Procedure Call (RPC)

Remote procedure Call (RPC) is one of the simplest API paradigms, in which a client executes a block of code on another server. RPC is all about *actions.* Clients typically pass a method name and arguments to the server and receive back JSON or XML.

* The endpoints contain the name of the operation to be executed.
    
* API calls are made with the HTTP verb that is most appropriate: GET for read-only requests and POST for others.
    

RPC styles are great to work with, due to their ability to expose a variety of actions that might have more nuances and complications than can be encapsulated with CRUD or for which there are side effects unrelated to the "resources" at hand. Although RPC style API also accommodates complicated resource models or actions upon multiple types of resources.

Slack's conversational API allows several actions like `archive, join, kick, leave, and rename`. Additionally, there are other actions, such as posting a message with chat.postMessage, which have complex relationships with message resources, attachment resources, and visibility settings within the web client.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687930127826/f39e1b96-9990-4f7f-b249-528e238d0c4d.png align="center")

## GraphQL

GraphQL is a query language for APIs that has gained significant traction recently. It was developed initially by Facebook in 2012 before being publically released in 2015 and has been adopted by API providers like GitHub, Yelp and Pinterest.

GraphQL allows users to define the structure of the data required, and the server returns exactly that structure.

`GraphQL query:--`

```graphql
{
 user (login: "Aryan"){
 id
 name
 comapny
 DateOfBirth
 }
}
```

`Response from GitHub GraphQL API:--`

```graphql
{
  "data:"{
    "user:"{
       "id": "GDXU76DNU5YMD15",
       "name": "Aryan Parashar",
       "comapny": "hashnode_blogger",
       "DateOfBirth": "01-01-2003"
     }
  }
}
```

GraphQL requires only one single URL endpoint and in addition to this feature you don't need to use different HTTP verbs to describe the operation instead, you indicate in the JSON body whether you're performing a query or a mutation.

`GraphQL API call to GitHub`

```graphql
POST /graphql
HOST api.github/json
Content-Type: application/json
Authorization: bearer 2342dg1ac7g7568345d7e
  xoxp-165093764-2178563478-1167892200-7865349
{
   "query": "query{viewer{login}}"
}
```

GraphQL has some key advantages leaving up no other option other than using it in place of other APIs with its users:--

1. GraphsQL enables clients to nest queries and fetch data across resources in a single request and thus the use of GraphQL can be quick, even on slow network connections.
    
2. We can add new fields and types to a GraphQL API without affecting existing queries.
    
3. One of the major advantages of using GraphQL is that we can use log analysis to analyze which clients are using a field so that if it isn't being used then it could be removed easily.
    
4. This log analysis and removal of unused fields eventually helps in reducing the payload capacity thus making them smaller in size.
    
5. GraphQl is also strongly typed which means that it is possible to find typos and type checking more easily thus helping in reducing the error occurrences.
    
6. GraphiQL is an in-browser IDE for exploring GraphQL which let users write, validate and test GraphQL queries in the browser.
    

**Disadvantage:--**

The server needs to do additional processing to parse complex queries and verify parameters. Initially, within a company, it is much easier to predict the use cases and debug performance bottlenecks while working with external developers it becomes much more difficult to understand those use cases.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687954412304/6e95d864-619d-4361-8400-875b74d87720.jpeg align="center")

# Event-Driven APIs

With the request-response APIs, for services with constantly changing data, the response can become stale(old or not fresh) quickly. To stay up to date, Developers manage to update the data by polling method in which the requests are made to check for updates from the server or endpoint periodically. It includes sending requests frequently in fixed intervals to stay updated at low and higher frequencies.

If developer poll at low frequency then, their app won't have data about all the channels that occurred in single polling. While if the polling is done at a higher frequency would eventually lead to wasting a large number of resources, as most API calls will not return any new data and are estimated to receive only 1.5% of the useful update.

To receive data about events in real-time certain different patterns and mechanisms are being adopted by companies and API providers based on their needs.

## WebHooks

A webhook is just a request-response HTTP acceptor URL that provides event updates based on the requests sent to the server in real time. It is used by many apps like Slack, Stripe, GitHub and Zapier for different functions.

Slack uses it by helping you to get notifications by configuring it to simply receive notifications whenever a new channel is being created.

Slack also build a system to retry the failed messages by this mechanism in cross-checking the data and message reachability by sending the request of the same message three times until a response is received at a fixed time interval.

it can certainly become noisy when each WebHook call represents n event but when there are thousands of events happening in a short time need to be sent via a single WebHook can surely turn out to be noisy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687954607613/e5511a33-7fb6-4a8a-aa73-f857b647fa21.jpeg align="center")

## WebSockets

WebSockets establishes a two-way streaming communication channel over a single Transport Control Protocol(TCP) connection which could be used between a client and a server or even server-server communication. The WebSocket protocol is supported by major browsers and is often used by real-time applications as well.

Slack uses WebSockets to send all notifications of the events taking place in the webspace to the clients and a real-time messaging API to developers in order to send events from Slack in real-time and send messages to users.

Trello uses WebSockets to send all the changes made by the users down from the servers to browsers listening on the appropriate channels.

Blockchain uses WebSockets to send real-time notifications about new transactions and blocks that took place.

WebSockets are great for live and fast streaming of data and long-lived connections but the disadvantage is seen if the end users' connectivity is a bit dull. there are also issues related to Scalability. App-Developers using Slack's API in their app are required to manage the connectivity between the Slack server and the app's server.

## HTTP Streaming

With the HTTP request-response APIs, clients are required to send requests to API servers to receive a response of a limited length. With the HTTP Streaming mechanism, the servers can continue to push new data in a single long-lived connection opened by the client. there are some options to manage the continuous flow of data from server to client:--

1. The server is required to set the Transfer-Encoding header is chunked which indicates to the client that the data will be received in chunks of newline-delimited strings.
    
2. To stream data by SSE(server-sent events) which is great for the consumers who are consuming these events on browsers because they can use the standardized EventSource API(which receives the notifications sent by the server).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687954699261/d2d639d2-5396-4083-9240-95d794dbee54.png align="center")

Twitter utilizes this protocol and the major advantage seen by the developers for this protocol which is responsible for delivering the data through a single connection opened between an app and Twitter's streaming API is they don't have to poll Twitter's API continuously for new tweets instead twitter's Streaming API can push new tweets over a single HTTP connection instead of a custom protocol which eventually saves a lot of resources for Twitter's developers.

But the Disadvantage seen for using this mechanism is that they might not need to start rendering data to the application until a threshold is met and thus Clients and proxies have a buffer limit. Another disadvantage is that if the client wants to change what kind of events they listen to, HTTP Streaming might not be a good choice as the event change requires reconnections and this mechanism is based on sending the same streaming data on the same single HTTP connection and the bidirectional communication is also difficult in HTTP Streaming which was much easier in case of WebSockets which could be understood by the below image.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687954540656/f4997aeb-af3a-4345-bd43-5d97053de0b4.png align="center")

In the end, it isn't compulsory to use a single mechanism or paradigm, you may use multiple paradigms and mechanisms to function in various different ways to perform different tasks like that by Slack, Github or Stripe and a lot more providers which you don't even know about yet.

Soon, I will be creating another blog about API security and the steps to create an API.

Hope you get to learn some from this blog for which you came here for 😄

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[Aryan\_2407](https://twitter.com/Aryan_2407)