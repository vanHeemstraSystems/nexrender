# 200 - Calling the Nexrender Server API with Node

Based on [Using API](https://github.com/inlife/nexrender?tab=readme-ov-file#using-api)

Now, after you've loaded up your worker and server nodes, they will need some jobs to be submitted to the server to start actual rendering. You can send a direct POST request from a Node application:

```
npm install @nexrender/api --save
```

```
const { createClient } = require('@nexrender/api')

const client = createClient({
    host: 'http://my.server.com:3050',
    secret: 'myapisecret',
})

const main = async () => {
    const result = await client.addJob({
        template: {
            src: 'http://my.server.com/assets/project.aep',
            composition: 'main',
        }
    })

    result.on('created', job => console.log('project has been created'))
    result.on('started', job => console.log('project rendering started'))
    result.on('progress', (job, percents) => console.log('project is at: ' + percents + '%'))
    result.on('finished', job => console.log('project rendering finished'))
    result.on('error', err => console.log('project rendering error', err))
}

main().catch(console.error)
```

app.js

Where you should replace the input for ```addJob``` with the following:

```
'{"template":{"src":"file://z/movie-digital-twin/digital-twin.aep","composition":"digital-twin"}}'
```

**TO DO**: Figure out how to point to the mapped network drive ...

Also replace the string ```my.server.com``` in all locations with the **hostname** or **IP address** of the Paperspace machine (here: ... , or 0.0.0.0 when called locally).
