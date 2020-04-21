### Inspired by https://github.com/LawJolla/prisma-auth0-example.git to migrate idiomatic fullstack GraphQL Auth/Roles pattern up to prisma2

# Initiative to PR to [prisma-examples](https://github.com/prisma/prisma-examples)

Target Pull Request:
https://github.com/prisma/prisma-examples/tree/master/typescript/graphql-auth0-roles

Layers:

---
This repo (The Auth0 React base) 

---
[LawJolla](https://github.com/LawJolla)'s prisma1 base [prisma-auth0-example]https://github.com/LawJolla/prisma-auth0-example.git()

---


## Goals of initiative:
  +  Community best practice patterns for implimenting role based Authorization in the context of a *full stack* example using GraphQl Apollo and Prisma2 ( G. A. P. stack )

---
---
---
Original Auth0 README.md bellow... followed by LawJolla's prisma-auth0-example README.md pasted below.

---

# Auth0 React Samples

[![CircleCI](https://circleci.com/gh/auth0-samples/auth0-react-samples.svg?style=svg)](https://circleci.com/gh/auth0-samples/auth0-react-samples)

This is the sample code for the [Auth0 React Quickstart](https://auth0.com/docs/quickstart/spa/react) using [auth0-spa-js](https://github.com/auth0/auth0-spa-js).

There are two sample applications:

- [Login](./01-Login) — demonstrates logging in and viewing profile information
- [Calling an API](./02-Calling-an-API) — demonstrates how to call a third-party API using access tokens

## What is Auth0?

Auth0 helps you to:

- Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, among others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
- Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
- Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
- Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
- Analytics of how, when and where users are logging in.
- Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a Free Auth0 Account

1. Go to [Auth0](https://auth0.com/signup) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to login.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## Author

[Auth0](https://auth0.com)

## License

This project is licensed under the MIT license. See the [LICENSE](./LICENSE) file for more info.

---
---
---
# Prisma React Auth0 Example
Video Demo

[![](http://img.youtube.com/vi/y1zBjWhfPzQ/0.jpg)](http://www.youtube.com/watch?v=y1zBjWhfPzQ "Auth0")

🚀 Basic starter code for a fullstack app based on Prisma, Auth0, React, GraphQL & Apollo Client.

## Goals

My idea of a possible authentication and authorization flow for Prisma's Instagram (blog?) clone. I am not an expert and put together this repo as a learning exercise. 

This repo follows the [Prisma Permissions](https://www.prismagraphql.com/docs/tutorials/graphql-server-development/permissions-thohp1zaih).

If you see any potential security issues, please let me know!
 
## Technologies

* **Frontend**
  * [React](https://facebook.github.io/react/): Frontend framework for building user interfaces
  * [Apollo Client](https://github.com/apollographql/apollo-client): Fully-featured, production ready caching GraphQL client
* **Backend**
  * [Auth0](http://www.auth0.com): Authentication as a service. (And this demo uses RS256 hotness!)
  * [Prisma](https://www.prismagraphql.com): Turns your database into a GraphQL API
  * [graphql-yoga](https://github.com/graphcool/graphql-yoga/): Fully-featured GraphQL server with focus on easy setup, performance & great developer experience
  * [prisma-binding](https://github.com/graphcool/prisma-binding): [GraphQL binding](https://blog.graph.cool/reusing-composing-graphql-apis-with-graphql-bindings-80a4aa37cff5) for Prisma services

## Requirements

You need to have the following things installed:

* Git
* Node 8+
* Prisma CLI: `npm i -g prisma`
* Auth0 account
* Basic Auth0 Console Knowledge -- this demo is short on how to configure the Auth0 console, but even a novice Auth0 user should get it.  I did!  This is my first project using Auth0.

## Getting started

```sh
# 1. Clone it
git clone git@github.com:LawJolla/prisma-auth0-example.git

# 2. Navigate into the folder
cd prisma-auth0-example

#3 Install dependencies.  NPM should work if not using yarn
yarn install

#4 Install server dependencies
cd server
yarn install

#5 Make .env file
touch .env

#6 open .env in your editor of choice, e.g.
code .env
```
Make your prisma secret
PRISMA_SECRET="myapp123"

```ssh

#7 Deploy Prisma cluster
prisma deploy

#8 Copy HTTP endpoint from Prisma, e.g. https://us1.prisma.sh... or localhost...

```

## .env file
Your .env now file now also needs the following:
``` 
PRISMA_ENDPOINT="YOUR_COPIED_ENDPOINT" # e.g. https://us1-prisma.sh...
AUTH0_DOMAIN="YOUR_AUTHO_DOMAN" # e.g. yourdomain.auth0.com
AUTH0_AUDIENCE="YOUR_API/AUDIENCE" # e.g. https://yourdomain.auth0.com/api/v2/
AUTH0_ISSUER="https://YOUR_AUTH0_DOMAIN" # e.g. https://yourdomain.auth0.com/
```
Your Auth0 console will provided the needed information above.

Make sure your audience is an API and not `https://...auth0.com/userinfo`.  That will not return an access token.  Only an API will.

```sh
#8 Start the server
yarn dev

#9 Configure your client Auth0 variables
cd ..
cd src/auth

#10 Create an auth0-variables file
touch auth0-variables

#11 Edit auth0-variables.js in your favorite editor, e.g.
code auth0-variables
```
## auth0-variables.js
Copy and paste the AUTH_CONFIG below, and fill in the variables, and save

```
export const AUTH_CONFIG = {
  api_audience: 'YOUR_API_AUDIENCE`, #same as above in server
  domain: 'YOUR_DOMAIN', // e.g. your-domain.auth0.com
  clientId: 'YOUR_CLIENT_ID', // e.g. string of characters from Auth0 for your API
  callbackUrl: "http://localhost:8000/callback" // make sure Auth0 has http://localhost:8000 as a callback url
}
```

```ssh
#11 Start the client
yarn start

#12 Navigate to localhost:8000

#13 See what errors you get 🤣
```

#Directive Permissions

This demo uses the new-ish GraphQL directive permission pattern.  Here's a great video from Ryan Chenkie, a developer at Auth0, describing how it works.

[![](http://img.youtube.com/vi/4_Bcw7BULC8/0.jpg)](https://www.youtube.com/watch?v=4_Bcw7BULC8 "Auth0")

Tl;dr:  Simply decorate your fields / queries / mutations with directives, and let the directive resolvers handle the rest!