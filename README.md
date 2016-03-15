# mzdemo

git clone https://github.com/bkoz/mzdemo.git

oc login

oc new-project mydemo

Choose php:5.6 builder image

Set name = mydemo
Set git url = https://github.com/bkoz/mzdemo.git

Copy the generic web hook url from the build config and add it to the github repo settings.

Now that the app is built and running, we'll make a src change.

Add a mysql-ephemeral pod

$ oc env dc mydemo (The app should pickup the kube env vars such as MYSQL_SERVICE_HOST, MYSQL_SERVICE_PORT

$ oc env dc mysql --list

$ oc env dc mydemo MYSQL_USER=userJ6J MYSQL_PASSWORD=qCQEegxm46XVcfeT MYSQL_DATABASE=sampledb

After pod is redeployed, fresh the web browser.

