The application allows you to manage SSL Certificates issued by Let’s Encrypt CA. The application uses the Let’s Encrypt ACME Client and also uses SQLite database backend to store additional information about SSL certificates.

![ScreenShot](http://genia.sk/wp-content/uploads/2016/01/022.png)


## Requirements ##
- Let's Encrypt ACME client, that is configured and able to issue certificates
- python
- CherryPy
- Some other Python libs
- openssl installed

## Basic features ##
- WEB GUI for overview and easy management
- HTTP API for automation
- Creating / Revoking / Re-Issuing of certificates via API
- Automatic renewal of existing certificates
- Logging of operations done with Certificates
- Logging of application HTTP access and runtime error
- Logging of debug responses from ACME Client
- Limiting Access for specific IP addressed


## Installation ##
The application was developed and tested on Debian Linux.
- Clone the repository.
- Edit the ALLOW_IPs=["x.x.x.x"] in file app.py
- Run "app.py".

On the first run, the application will create the required SQLite database file.
Navigate your browser to: http://x.x.x.x:9181/ to access the GUI.

## Domain Validation (Authentication) via Webroot ##
To be able to issue certificates you shoud run an Apache server with empty webroot. (default on Debian)
Then redirect all request from http://domain-to-issue.tld/.well-known/acme-challenge to the same machine where you host the Management application.

### NGINX Config example ###
	location /.well-known/acme-challenge{
	    proxy_redirect off;
	    proxy_pass http://x.x.x.x:80;
	    expires off;
	    allow all;
	    }


## Documentation ##
The documentation for API calls are included in the application itself. Look for the “API Documentation” tab in main menu.

Have fun!


## Comercial Support and Advanced features ##
We also maintain an Advanced version fork that has the following features:
- Email notifications (Informations and Errors while issuing certificates).
- Maintenance module (designed to simplify management for Webhosters).
- Profesional support!
- Customisations and implementation help.

Contact me if you interested in Support, Customisation or Advanced Version

email: tomas@dobrotka.sk

web: www.dobrotka.sk

Homepage of the App: http://genia.sk/lets-encrypt-certificates-management-console-api/


