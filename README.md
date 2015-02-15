# SocialAuthDjangoTutorial


## Introduction

A simple example for beginners to implement social authentication in their Django Projects.
In this tutorial, we will teach you how to sign up/in with facebook, twitter and Google with your web applications.

After we finish the basic sign in mechanisms in those three platforms, 
the next step is to learn how to get users' profile image from social networks as their profile image in our web services. 

## First Step: Install the Python Social Auth

### 1. Install From pypi:
    
    $ pip install python-social-auth
    
  
You can also install social-auth from github clone, check [here](http://psa.matiasaguirre.net/docs/installing.html#dependencies)

### 2. Set up the social apps in our django projects

##### A. Set up the INSTALLED_APPS in your setting.py

If you use the default django ORM, please follow:

    INSTALLED_APPS = (
    ...
    # Use default Django ORM
    'social.apps.django_app.default',
    ...
    )
    
Using MongoEngine? Follow the below setting:

    INSTALLED_APPS = (
    ...
    # For MongoEngine
    # 'social.apps.django_app.me',
    ...
    )

After the setting, do the migration to create tables the social auth need.
    
    $ python manage.py migrate

Then go to check our database( I like postgreSQL :) ), we can see that there are 4 tables established with prefix "soical_auth".

![database_picture](https://raw.githubusercontent.com/davisfreeman1015/SocialAuthDjangoTutorial/master/Imgs/NewDatabaseTables.png)
##### B. Add desired authentication backends to Django's AUTHENTICATION_BACKENDS setting:

Social Auth provides many social networks' authentications. Facebook, Twitter, Google, Yahoo, Spotify and Instagram are all supported. We can check whether the social authentications are supported by Social Auth in [here](http://psa.matiasaguirre.net/docs/intro.html#features)  
   
In this tutorial, we will focus on making a Web app with Facebook, Google and Twitter authentications.

    
    # Authentication backends Setting
    AUTHENTICATION_BACKENDS = (
    # For Facebook Authentication
    'social.backends.facebook.FacebookOAuth2',
    
    # For Twitter Authentication
    'social.backends.twitter.TwitterOAuth',
    
    # For Google Authentication
    'social.backends.google.GoogleOpenId',
    'social.backends.google.GoogleOAuth2',
    'social.backends.google.GoogleOAuth',
    
    # Default Django Auth Backends
    'django.contrib.auth.backends.ModelBackend',
    )

###### Warning: In the tutorial, we use django's authentication system. If you have make a better authentication system on your own. Hope you can share us how to implement customized authentication system with Social Auth :)

##### C. Add desired authentication backends to Django's AUTHENTICATION_BACKENDS setting: