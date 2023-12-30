# Message Server

## Introduction

- I made this project for Makers Module 5 - Cloud Deployment: Connecting to a Database & Removing Secrets
- This is a simple web app that allows the user to input a message and display it.
- It is containerised with Docker using the `Dockerfile`.
- It uses Exoframe (Maker's toy cloud hosting system) to deploy to the cloud.

## Objectives

I used this project to learn to:
- [x] Explain how data is persisted in the cloud.
- [x] Set up a cloud deployment with a database.
- [x] Explain how secrets are removed from config and code.

## Setup

To run this project locally:

```bash
; cd ../web
; pipenv install
; pipenv shell
; python app.py    # Run the server
```
To deploy with Exoframe (Maker's toy cloud hosting system):
```bash
# Install NodeJS
; brew install node

# Install exoframe
; npm install exoframe -g

# Log in to the Makers exoframe server (this uses a .pem file given to me by Makers)
; exoframe login https://exoframe.xf.mkrs.link -k path/to/key.pem
Endpoint URL updated!
Logging in to: https://exoframe.xf.mkrs.link
? Username: # use natalieclark
Successfully logged in!

# Check it works
; exoframe ls 
No deployments found on https://exoframe.xf.mkrs.link!

# Set the environment variable database password in the exoframe secrets database
; exoframe secret set natalieclark-postgres-password PASSWORD # Substitute PASSWORD with the actual password!

# Deploy the database
; cd db
; exoframe deploy

# Deploy the app
; cd ../web
; exoframe deploy

# Visit the URL to see the app running
; open https://https://natalieclark-messages.xf.mkrs.link

# When you want to update your server with the latest code, run:
; cd db
; exoframe deploy --update
; cd ../web
; exoframe deploy --update
```
