# Amitruck 2.0 - Authentication and Authorization API Documentation

<div align="center">
	<br>
	<br>
	<img width="360" src="Assets/Amitruck%202.0%20Logo.png" alt="apidoc-markdown logo" />
	<br>
	<br>

📝 This is the official Amitruck 2.0 Authentication and Authorization APIs Documentation

## Badges will go here

<!-- [![Node.js CI](https://github.com/rigwild/apidoc-markdown/workflows/Node.js%20CI/badge.svg)](https://github.com/rigwild/apidoc-markdown/actions)
[![npm package](https://img.shields.io/npm/v/apidoc-markdown.svg?logo=npm)](https://www.npmjs.com/package/apidoc-markdown)
[![npm downloads](https://img.shields.io/npm/dw/apidoc-markdown)](https://www.npmjs.com/package/apidoc-markdown)
[![license](https://img.shields.io/npm/l/apidoc-markdown?color=blue)](./LICENSE) -->

</div>

# Introduction

Welcome to Amitruck 2.0 Authentication and Authorization Service. This service requires users to register their applications first before they can be able to use our service.

Applications are registered using django o-auth service which provides a user interface where a user must enter their application name. Applications in this case could be mobile or web applications. Django o-auth service automatically provides Client id and Client secret after the application name field. At this point, the user should take note of this two very important fields by copying them in a separate file. This fields will be used to generate a token that will allow the user to access all other APIs. Next, the user will be required to select the client type.
The client type should be confidential in this case. This is because we want to ensure the security of the application.

# Step 0ne

Next the user is required to select the Authorization grant type which is this case is Resource owner passsword-based. Here we are maing use of password as the grant type when generating the token.

Next the user will fill in the Redirect uris e.g https://dev.api.amitruck.co/v2/auth/user/redirect/. Redirect URIs are used by our OAuth authentication service as a security measure. ORCID will only send authenticating users to URIs registered by the client requesting authentication. This prevents services from impersonating each other. See the screenshot below. Before saving the application, please note down the CLIENT_ID AND CLIENT SECRET in a separate file.` Please make sure this two variables are only known to you`. Congrats you have made your first application.

<div align="center">
	<br>
	<br>
	<img width="360" src="Assets/app.png" alt="apidoc-markdown logo" />
	<br>
	<br>

</div>

# Step Two

You will now start your Postman on your local machine. In this case a postman Collection will have been shared with you. We shall start by generating a token inorder to be able to use other APIs. Head to the GET TOKEN request on postman. The url should be ` https://dev.api.amitruck.co/v2/auth/user/o-auth/token/`

The body of this should be as shown below. The body contains superuser credentials as shown in the example blow:

<div align="center">
	<br>
	<br>
	<img width="660" src="Assets/token.png" alt="apidoc-markdown logo" />
	<br>
	<br>

</div>

The next step is very important inorder for us to get the access_token. For you to get the token, thr client_id and client token we got from step one are required. As seen in the screenshot below, we use the client_id as the username and client secret as the password in the Auth section using Basic Auth type.

<div align="center">
	<br>
	<br>
	<img width="660" src="Assets/generate.png" alt="apidoc-markdown logo" />
	<br>
	<br>

</div>

Once this is done, go ahead and make the request by pressing the send button. If all parameters you passsed are correct you should get a response as shown below with ` access_token`, ` expires_in`, ` token_type`, ` scope` and ` refresh_token`.

```ts
{
    "access_token": "DfpgIlRgMKenGagBCbOZl1JC7kMeVh",
    "expires_in": 36000,
    "token_type": "Bearer",
    "scope": "read write groups",
    "refresh_token": "v26jHOfmd1hXV97iLoyAVJrZgXWdtZ"
}
```
