# 100 - Calling the Nexrender Server API with CURL

Based on [Using API](https://github.com/inlife/nexrender?tab=readme-ov-file#using-api)

Now, after you've loaded up your worker and server nodes, they will need some jobs to be submitted to the server to start actual rendering. You can send a direct POST request:

```
curl \
    --request POST \
    --header "nexrender-secret: myapisecret" \
    --header "content-type: application/json" \
    --data '{"template":{"src":"http://my.server.com/assets/project.aep","composition":"main"}}' \
    http://my.server.com:3050/api/v1/jobs
```

Where you should replace the string for ```data``` with the following:

```
'{"template":{"src":"file://z/movie-digital-twin/digital-twin.aep","composition":"digital-twin"}}'
```

**TO DO**: Figure out how to point to the mapped network drive ...

Also replace the string ```my.server.com``` in all locations with the **hostname** or **IP address** of the Paperspace machine (here: ... , or 0.0.0.0 when called locally).
