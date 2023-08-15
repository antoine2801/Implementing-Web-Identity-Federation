<h1>Implementing Web Identity Federation </h1>



<h2>Description</h2>
n your on-premises network and Amazon Web Services (AWS) cloud infrastructure. Source : https://learn.cantrill.io/

<h2>Languages and Utilities Used</h2>

- <b>Python</b> 


<h2>Environments Used </h2>

- <b>AWS</b> 

<h2>Project walk-through:</h2>

<p align="center"> 
 <h3> Some definitions <h3/>

- Identity Federation is a process where external identities are used instead of services maintening their own identities. Better exeperience for customer and less admin overheaf for services

- 3 components : customers, Service Provider, Identify Provider ( Identify Providers can use enterprise standards  such as SAML or can be Web Identity Providers such as Google, Facebook or Twitter
- 5 steps : (1) Customer open a service (2) Service delivers login form using IdP (3) Customer login using IdP which delivers a 'token' if successful (4) IdP Token is delivered back to the service (5) The SP trusts the IdP - Idp generated tokens can be used instead of application logins
- Benefices : Reduce the number of login for customer, Reducer barrier to entry, More secure - login managed externally, Less admin overhead, Scalable - beyond any AWS limits, Operate with existinhg single source of truth enterprise ID stores

<h3> Amazon Cognito <h3/>
  
- Authentification, Authorization, and user management
- User pool - Sign-in and get Json Web Token 
- Identity pool - Allow you to offer access to Temporary AWS Credentials 
- Unauthenticated Identities - Guest Users 
- Federated Identities : Google, Facebook, Twitter, SAML2.0 and User Pool for short term Aws Credentials to access AWS Resources
<img src="https://i.imgur.com/Yt0Y7yh.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
source : cantrill


  <h3> Implementing Web Identity Federation : Project baselines <h3/>
  
- Anonymous user  access to bucket with private patches is denied
- HTML and JS loaded from S3 bucket via CloudFront into browser
- User directed at Google IdP to authenticate
- If successful a google token is returned
- Cognito API Called, using a configured ID pool to swap Google token for AWS credential
- Cognito Assumes IAM role, AWS temporary credentials are generated
- Credentials returned to User 
- AWS Credentials are used to access S3 bucket with private patches 


  <h3> Implementing Web Identity Federation: Generate API to connect to Google <h3/>
<img src="https://i.imgur.com/KYyLfBD.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

<h3> Implementing Web Identity Federation: Create/Config AWS Cognito <h3/>
<img src="https://i.imgur.com/pt9nm3u.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/BRfi5s5.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/n25LET0.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/zjCIY1q.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/kx21frL.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/w9YsFgS.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

<h3> Implementing Web Identity Federation: Config HTML and JavaScript to interact with Google IP <h3/>

<img src="https://i.imgur.com/iKUWRwu.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

  

  




<br />
