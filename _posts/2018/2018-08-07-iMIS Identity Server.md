---
layout: page
subheadline: 
title:  "iMIS Identity Server"
teaser: "Mobile apps and external javascript apps are not currently supported by iMIS.  You would need to implement a server side component on your end."
meta_teaser: "meta teaser"
breadcrumb: false
categories:
    - SSO
    - iMIS
tags:
    - blog
    - content
    - post
    - post format
image:
    title: gallery-example-1.jpg
    caption: Unsplash.com
    caption_url: http://unsplash.com
author: Eddie Brady
---

# Integration Concerns
To provide some perspective, there are two main concerns when integrating with iMIS using an external application:

1. **User Identity**

	We need a way for our application to establish the users identity.  That application may be a native app (mobile or desktop), a javascript app, or a server side app.
	
2. **Access Tokens (OAuth 2)**

    We need to obtain an access token in order to call the iMIS API.
    An access token can represent either
	a. the logged in user
	b. the client application

# OAuth 2 Flows

APIs are usually secured by OAuth 2 using access tokens.  Oauth 2 supports 4 types of flows for obtaining an access token.  I will simply list them here and not describe them.  There are many resources that already describe them.

1. Resource Owner
2. Client Credential
3. Authorization Code
4. Implicit

# iMIS & OAuth 2

The iMIS Token endpoint supports the Resource Owner flow for two different use cases.

**Use Case 1 - Remote Service** 

	a. Create an "application user" in iMIS with a username and password. 
	b. Assign the RemoteService role to that "application user".  
    c. Aapplication(s) can now use this username and password to obtain an access token.
	
	grant_type=password
	username=###
	password=###
	
	* This approach supports service side apps only because you need to be able to keep the username and password secure.
	* The access token does not represent the logged in user.  Instead it represents the fictitious "application user" that was defined for this purpose.
	* Permissions are restricted based on how you defined the permissions in iMIS for the "application user".

**Use Case 2 - SSO iPart** 

a. Using the SSO iPart, iMIS implements the Resource Owner flow and ultimately passes back the refresh token to the application.  
b. The application can then use the refresh token to obtain an access token.  The token endpoint responds with not only an access token but a few other properties as well, such as a new refresh token and the user name, which we can use to "establish identity".  Technically, this is a misuse of OAuth 2 as OAuth 2 is not supposed to be used for authentication.

	grant_type=refresh_token
	client_id=###
	client_secret=###
	refresh_token=###
	
	* This approach is a server side approach because it requires a client id and client secret. 
	* Additionally, a "user agent" is required to implement the flow.
	* After exchanging the refresh token you get an access token in the response and the "user id".
	* The access token represents the logged in user.

# OpenID Connect

OpenID Connect is the preferred way to establish identity.  OpenID Connect adds authentication on top of OAuth 2.  When using OpenID Connect your application will recieve an Identity Token and an Access Token.  The Identity Token is cryptographically linked to the access token and can be used by your application to establish identity.

# iMIS Identity Server
We were facing similar issues with authenticating external applications.  We solved them by creating iMIS Identity Server.  iMIS Identity Server adds OpenID Connect support to iMIS.  With iMIS Identity Server you can support any use case that you encounter.  You can learn more here
http://www.organizedbits.com/imis-identity-server.html

**The Benefits**

The benefits of iMIS Identity Server are that
1. It allows you to secure all type of applications (native/mobile apps, js apps, and server side web apps)
2. It supports Single Sign On and Single Sign Off between iMIS and 3rd party applications.
3. Additionally, it allows you to build and secure your own APIs if desired.

If you'd like more information please reach out to us.

