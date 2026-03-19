
OAuth is an open-standard authorization protocol that allows application to access user data without requiring the user's password. 
It enables secure delegate access, commonly seen in "Login with google/facebook" button. 

- Prevents sharing passwords with every app.
- To allow safe, controlled access to user data. 
- User access tokens by authorization server. 


## OAuth Components

### OAuth Provider(Authorization Server)

The server that verifies user's identity and issues access/refresh tokens. 

- Store and protect user account and data. 
- Handles Login(Authentication) 


### OAuth Client(Third Party application)

The application that requests access to the user's data from the OAuth Provider. 

- Redirects the user to the providers login
- Never sees user's password

### Resource Owner(user)


# Types of Auth Tokens

#### **Access Tokens:**
A Short lived token that allows the client to access protected APIs on behalf of the user. 

- Typically valid for minutes to hour. 
- Send with every API request
- Cannot be used to refresh or extend sessions


#### **Refresh Tokens**

A long lived Token that is used to obtain access to the user data without asking the user to login again. 

- Valid for days , months or until revoked. 

