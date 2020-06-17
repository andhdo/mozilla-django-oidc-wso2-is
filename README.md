# mozilla-django-oidc-wso2-is
(mozilla django oidc with wso2 / configuration reference)

# ServiceProvider Registration
## Identity Server configuration (wso2-is v5.11.0)
In side menu of wso2 identity server administration console, select ServiceProvider/add option

Add a brand new sp declaration



Go to the next tab, where is requested information of Oauth/OpenIdConnect (expand the options to go to details). Then click on “configure” option

A new dialog opens, that let we can register a new application
Fill the callback url field

And in the issuer token field, select JWT


Verify that option “Use SP JWKS endpoint” is selected (if it is visible. It could change in future versions)
Also verify encryption type, to become S256


Click in “add" button



So now we have created the sp. 
Now, we must create the claims.
For both django application and mozilla-django-oidc, name and email are required, so we aregoing to include both fields inside the claim usage of this service provider. 
So we go to the claims section, and select: 
http://wso2.org/claims/emailaddress . Then click on “dd claim URI” option. 
http://wso2.org/claims/username.  Then click on “dd claim URI” option

When an additional panel is displayed we mark those claims as required

We also select the claim dialect. In ths case is http://wso2.org/claims

Then save the configuration for the service provider


For the oauth2 protocol, client requires a key and a secret, that you can get in the bottom panel of the configuration, with this appearance: 


## Service Provider Config (django with mozilla-django-oidc)
This is the configuration variables used for the test. Don’t forget to not have this variables in the source code. As an alternative you can reference environment variables (os.environ).


Then execute the SP validating that you can get the user/email : 

Then execute the logout procedure.

