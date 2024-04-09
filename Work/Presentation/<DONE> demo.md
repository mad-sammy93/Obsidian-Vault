- Welcome to the frontend part of the project
	  - reset 
	  - set  
	  - login
	  - user list 
	  - add user
	  - show swagger
	
  ###  before login
  Thanks weinschel
  Welcome to the frontend part of the project
	- I just wanted to start by saying The application is designed internally by our own team
	- so far all screens have been converted and available as pages
	- over last 2 weeks the effort has been to integrate the backend with frontend
	- while we havnt been able to do so completely for user module,  we managed to integrate the majority of the functionality for the user module
	- also substantial work is done by backend team
	- critical work like authentication and logging
	- For this demo we are currently running the demo with my local machine
	- while the staging exist we haven't been able to deploy to the staging due to pending PR's


  - ##### For the login screen
		 ## [ login screen]
	  - We have setup the project login screen with 2 step authentication to enforce an extra security to the project which we will see in a while
	  - ## [ reset password screen]
	  - We also have the reset password screen
	  - where the user or admin will be able to request for a password change
	  - ### [show mainhog]
	  - we will receive a reset password link
	  - this will have a reset token which will be used to set new password

	  
	  - ## [ set password screen]
	  - while entering the new password screen 
	  - we have validations set to check the password set
	  - ## [ success screen]


	 - ### [login screen]
		**login**
		- After we enter a email and password 
		- we are take the the otp screen as part of 2factor  authentication 
		- we are sent an email with an otp code
		- once successfull we are taken to the Welcome screen

- ### [Dashboard screen]
  ### [User litsing screen]
- show user listing with columns
   ### [add User screen]

	- on click of edit we can edit user details

    
    [show swagger]
    Although we have currently not integrated the add new user screen
    I can show you the add user in swagger
    
    
```
{
  "firstName": "Adam",
  "lastName": "Tzur",
  "email": "adam@smartshore.nl",
  "mobile": "+918906785678",
  "userType": "admin",
  "companyId": 1,
  "projects": [
    {
      "projectId": 1,
      "roleId": 1
    }
  ]
}
```


[show other listing screens]
Althoght we cannot show the other screens since the api's are not ready
we are ready with all the screens to integrate it
[Over to weinschel]


    
    
    