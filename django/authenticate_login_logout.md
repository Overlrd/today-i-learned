#Authenticate , login and logout in django

At least any website have a register and login form.
While coding with PHP i used to code the login and register modules from scratch.
But *Django* provides highly efficient ways to deal with authentication with some built-in functions :
<br/>
 - **authenticate**   to check the user's credentials
	args : authenticate(request, some_field(usern_name-email), password )
 - **login**          to sign the user in after authentication
	args : login(request, user(django.contrib.auth.models.User object from the authenticate function) )
 - **logout**	      to log out the user
	args : logout(request)
