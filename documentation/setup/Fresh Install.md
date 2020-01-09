# Steps to Setup a fresh Pusher System

## Set up Ubuntu 18.04 server
* Set up users
* Harden security
* Configure ssh to allow only ssh key authentication
* Disable root login
* Add ssh keys
* Create pusher user, add sudo capability
* Generate ssh key for your pusher user

## Install packages
* git
* php (7.4 at least)
* node
* composer

## Install Pusher
Clone pusher repo to `/home/pusher/pusher-system` directory.

Add `/home/pusher/pusher-system` path is added to the pusher user's PATH to allow for script execution

# To create individual pipelines:
* ssh to server of website, add pusher ssh public key
* ssh to pusher box

## Run `env-setup-rsync` script
This will prompt you for the following information (examples in parenthesis)

* project name (projectname)
* environment (staging)
* repo url (git@github.com:organization/project.git)
* server alias (projectname-staging)
* server ip (127.0.0.1, whatever the ssh hostname is)
* server port (default is port 22)
* server username (whatever username is needed to ssh in)

Once setup is complete, ssh once into the web server by typing the ssh alias (ssh projectname-staging) and accepting the connection.

Head to Buddy and create a project and connect to the github repo.

Create a pipeline and copy the actions from the Zeek Buddy deployment steps. Be sure to change the appropriate connection parameters for the pusher box to the new box that was set up including hostname, port, user, etc. 

Inside of the pipeline's pusher action, grab the ssh key that Buddy shows, ssh to the pusher server and add the ssh key to the pusher user. This allows the Buddy ssh action to ssh into the pusher box and execute the deploy command.

