### what to do if a person refreshes the page staying on OTP or changes url

As of now I can think of two options to handle the refreshing of the page:  
1) Redirect to login page again  
2) Need to store info on the login page temporarily on permanent storage like localstorage and then remove it once the user is redirected to the dashboard


#### technically right now we need to redirect to the login screen and for that we can show a related message to the user if he tries to refresh or goes to another url