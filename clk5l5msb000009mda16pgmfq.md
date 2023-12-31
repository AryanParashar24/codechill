---
title: "Securing APIs : The Most Crucial Task of All"
seoTitle: "Securing APIs : The Most Crucial Task of All"
seoDescription: "Various methods by which your API Security can be enhanced & chances of data getting corrupted can be decreased with real lyf examples of big tech Players"
datePublished: Sun Jul 16 2023 15:22:38 GMT+0000 (Coordinated Universal Time)
cuid: clk5l5msb000009mda16pgmfq
slug: securing-apis-the-most-crucial-task-of-all
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689520446391/49db7145-eaba-4fab-aba9-f229fc1cb663.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689520633399/5c16bd2f-7d6c-4099-bbf9-a40e97f39a64.jpeg
tags: web-development, backend, apis, hashnode, wemakedevs

---

API Security is the most crucial task in the handling and managing of APIs. It's important to save your APIs from attackers which might result in data breaches and cause harm to your client's belief in you that's why it's an important task in building up your reputation and securing it by building protective security layers for your API at required different endpoints and stages.

There are various steps you need to implement in order to increase security like including input validations using Secure Socket Layer (SSL) protocol layer everywhere, maintaining audit logs, and protecting against cross-site request forgery (CSRF) and cross-site scripting (XSS).

**Security is maintained based on two fundamental elements:--**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689520595556/ebdfc1f9-2213-49fc-96c7-2b2874036e48.jpeg align="center")

## Authentication

The process of verifying who you are is exercised by web applications by asking you to log in with a username and password which is checked against an existing valid username/ password record to ensure the request is authentic.

## Authorization

The process of verifying that you are permitted to do what you asked for or trying to do. Some web applications only allow administrators to edit a web page while allowing normal users to just read them and access information out of them and that's what is referred to as **Authorization**.

Earlier, API providers adopted **Basic Authentication** which is the simplest technique to enforce access control to the web. The client sends an HTTP request with an Authentication header which consists of the word **"Basic"** followed by a space and a string generated by combining **username** and **password** with a colon and encoding it with base64 as:-

`Authorisation: Basic dxNLcjpwYXNzd29yZA`

This method provides the least amount of security as if you use a third-party developer's application, your users might need to share their username and password credentials with them which might create a lot of security chaos and risk private user data with malicious hackers. Applications get full access to your accounts and users cannot limit access to selected resources.

\*\*As a result **Twitter** decided to discontinue support for Basic Authentication for its core API in 2010.\*\*

# OAuth

To get rid of the problems faced by Basic Authentication, OAuth was introduced in 2007 which is an open standard that allows users to grant access to applications without sharing passwords with them.

The latest version in use is OAuth2.0 which is adopted by several big Champs of the industry like Amazon, Google, Stripe, Facebook, GitHub and Slack. It also allows API providers' users to grant selective permissions. All different applications have different resource requirements from their users and the OAuth framework enables API providers to grant access to one or more resources.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689505926144/99180cff-e93d-4306-9cb4-4c0f6d03aa5d.png align="center")

As depicted in the picture above, the application would receive permission to read a user's profile, friend list, or more, but it cannot post on the user's behalf. In the future, if users want to revoke the application's access to their user data, they can simply go to Facebook settings and revoke it without changing their passwords.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689484064192/4aae57aa-65db-4880-8a99-8f8a8606951b.png align="center")

# Token Generation

With OAuth, applications use an access token to call APIs on behalf of a user. Before an application can start accessing the OAuth flow, it needs to register with the API provider. During registrations, Developers provide a redirect URL- an application URL to which the API provider can redirect authorizing users. The API provider issues a client ID and client secret that are unique to the application.

An access token can be generated by the following steps after the application is registered:-

1. **The Application directs the user to the API provider for authorization.**
    
    The application first shows up the user a "Continue with Facebook"(as an example) on the screen, which redirects the user to the API provider's authorization URL. The application sends the ClientID, the permissions requested in a parameter called a scope, an optional unique string state parameter, and a redirect URL.
    
2. **API provider seeks the user's authorization.**
    
    The API provider should clearly indicate what \[permission the application is requesting. If the user denies the request for granting permission to access information from the selected API provider profile then the user is redirected back to the application's redirect URL with an access\_denied error. If the user approves the request, then the user is redirected back to the application with an authorization code.
    
3. **The application exchanges an authorization code for an access token**.
    
    The authorization code is exchanged via an access token. The application token will need to send the clientID, client secret, authorization code, and redirect URL to the API provider to receive an access token. The authorization code provided can be used only once; this help in preventing replay attacks. Applications can then use this access token for accessing protected resources on behalf of the user.
    

# Scopes

OAuth scopes are used to limit an application's access to user data. If an application only needs to identify a user they might only need the general user's profile information rather than asking for access to all of their information, by using granular OAuth scope. During authorization, the API provider will display all the scopes of the user. This way the user would be able to know what permissions are they granting to the application.

Twitter API offers three levels of permissions via scopes:

* Read Only
    
* Read and Write
    
* Read, Write and Access direct messages
    

Mostly API providers try to ignore the scopes and open up their APIs and start realizing the importance of it when their API is started getting adopted or getting abused by various practices, but the introduction of scopes becomes very complicated at that time.

Granular Scopes helps you ensure the applications have only the permissions they need. too many scopes can also create confusion for users and developers.

# Token and Scope Validation

After developers have received an access token from users after they have granted permission to access their information to the API providers, they can begin making API requests using this access by setting the HTTP Authorization header.

There are some things that the API providers need to keep in mind:

1. The access token is valid or not which is checked by matching the access token with the granted access token in your database.
    
2. The access token has the required scope for the action that the request is supposed to perform. If either check fails, the server should return an error along with some more data providing all information about the data which was asked in the scope and which was being provided to the API providers. Many companies like **GitHub** and **Slack** perform this action of providing important metadata along with the error by providing these two headers:
    
    * **X-OAuth- Scopes** lists the scopes for which a token has been authorized.
        
    * **X-Accepted-OAuth-Scopes** lists the scopes that the action requires.
        

Slack returns verbose errors in case the required scope dosen't match with the information in the provided-one as:

```json
{
    "ok": false,
    "error": "missing_scope",
    "needed": "chat:write:user",
    "provided": "identify,bot,users:read",
}
```

# Token Expiry and Refresh Token

The OAuth protocol allows limiting the validity of the access token issued in the OAuth flow. This way, if a token is compromised, the impact can be contained. If you issue an access token with limited validity, you need to provide a way for an application to obtain a new token, typically without intervention from the end user. One way to do this is by issuing refresh tokens.

A refresh token is a special type of token that is obtained to obtain a new access token and the current access token expires. Applications have to provide clientID, client secret and refresh token to get a new access token. API providers like **Google**, **Stripe**, **Salesforce** and **amazon** support the use of refresh tokens. Even if the access token is not expired it's a good habit to generate a new access token so that in case of a compromise, developers can rotate the existing access token and generate a new one.

Short-lived access token are more secure for the following reasons:

* if an access token is compromised, it will work only until it expires.
    
* If a refresh token is compromised, it will be useless without the client secret, which is typically not stored along with access tokens and refresh tokens.
    
* If both the refresh token and the client secret are compromised and the attacker generates a new token, the compromise can potentially be detected because typically refresh tokens are for one-time use only and only one party can use the API at a time.
    

## Revoking an Authorization

A user might want to know which applications are getting access to his profile's information and wants to revoke or cancel access, thus many API providers typically offer a page listing all the applications which are getting access to his information and an option to revoke authorization for those applications.

# WebHooks Security

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689520318296/63fb4048-07d9-49eb-a385-5f6e959ff53e.jpeg align="center")

The WebHook URLs are generally public and thus it is generally important for developers to be able to ensure the POST request came from the authorized sender as in the absence of this security verification an attacker might forge a request to the WebHooks URL.

## Verfification Token

A verification token is a secret shared between the API providers and applications. Slack sends a verification token which checks the token received with the request of the recorded value. If they don't match, the application ignores the request. This way, an application can verify if the request came from Slack or not. However, verification tokens also offer limited security because they are sent in plaintext with every request. If a verification token is leaked or compromised, an attacker can forge WebHooks requests.

# Request Signing and WebHooks Signatures

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689520379674/9442cf6c-431b-4747-9e08-bf0d3142f87f.jpeg align="center")

Webhooks payloads are typically signed by computing a hash-based message authentication code (HMAC) of a shared secret plus the request body, and the signature is sent as a part of the request header. API providers like Stripe and GitHub use this information to secure WebHooks.

Attackers often also send back or retransmitted a WebHook with a valid signature to resist this form of attack many providers often use a request timestamp in the message payload. If the time stamp is too old, applications can reject the request.

# Mutual Transport Layer Security

When you connect to an https:// URL with the Transport Layer Security(TLS) Handshake protocol, the server sends its certificate to the client. the client then verifies the server's certificate before trusting the response.

With a mutual TLS, the server and client both authenticate each other by, the server sending the client a certificate request and the client responds with a certificate. The server verifies the client's certificate before trusting the request.

You can implement local TLS at a lower level and developers can enforce high security while opening a firewall for an API without requiring anything of the application developers.

# Thin Payloads and API Retrieval

Different application developers might be using different security layers to protect WebHooks and it can create chaos of confusion whether they are verifying WebHooks requests.

A more secure option is to send limited information to the payload indicating to the application that something has changed. To retrieve the full event, the application would need to make a subsequent request to the web API. The key benefit of using this approach is that even if applications do not verify WebHooks, they will receive the full event only after making regular authenticated requests to a web API.

Google uses this method for securing WebHooks. Gmail's API allows applications to subscribe to watch for changes in an inbox using WebHooks. When something changes, GMail sends a WebHooks request, including the email address and an ID for the change. Applications can call Gmail's history.list web API to retrieve the full change details like:

```json
{
 message:
 {
 data: "eyJlbWFpbEFkZHJlc3MiOiAidXNlckBleGFtcGxlLmNvbSIsICJoaXN0bz",
 message_id: "1234567890",
 }
 subscription: "mysubscription"
}
```

If you wish to know about the basic architecture and various types of API Paradigms and polling alternatives please have a look at my other blog as well, i m sure u will love it😄😄

%[https://codechill.hashnode.dev/api-101-introduction-imp-of-api-paradigms] 

Hope you get to learn some from this blog for which you came here 😄

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[Aryan\_2407](https://twitter.com/Aryan_2407)