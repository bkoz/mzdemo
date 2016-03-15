# mzdemo

```
git clone https://github.com/bkoz/mzdemo.git
cd mzdemo
```

```
oc login
oc new-project mydemo
```

Choose php:5.6 builder image

Set name = mydemo
Set git url = https://github.com/bkoz/mzdemo.git

From the web console, we'll add a mysql-ephemeral pod and let it build and deploy. Set MYSQL_USER=user MYSQL_PASSWORD=password MYSQL_DATABASE=sampledb

Copy the generic web hook url from the build config and add it to the github repo settings.

Now that the app is built and running, we'll make a src change.

Redeploying the app will cause the kube env vars such as MYSQL_SERVICE_HOST, MYSQL_SERVICE_PORT to appear.

```
$ oc deploy mydemo --latest (or use the web console)
```

```
$ oc env dc mysql --list
```

```
$ oc env dc mydemo MYSQL_USER=user MYSQL_PASSWORD=password MYSQL_DATABASE=sampledb
```

After pod is redeployed, fresh the web browser.

Scale out the front end from the web console.

```
$ oc get pods -o wide -w
```

```
$ for i in `seq 1 10`; do curl http://mydemo-mydemo.apps.haveopen.com; done
```


