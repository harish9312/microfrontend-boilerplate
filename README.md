## Start editing the /config/webpack.config.js line 

* Edit the below content to expose the Component and Remote the same

```javascript
new ModuleFederationPlugin({
    name: "mf-boilerplate", // Current App name
    filename: "remoteEntry.js", // filename
    remotes: {}, // the micro frontends to use in container the things which we want import from other 
    exposes: {
        './Components': './src/mountContainer'
    }, // to give components to other services
    shared: {
        react: {
            singleton: true,
            eager: true,
            requiredVersion: deps.react,
        },
        "react-dom": {
            singleton: true,
            eager: true,
            requiredVersion: deps["react-dom"],
        },
    },
}),
```

* Change the entry point in webapck LN - 206

```javascript
// This means they will be the "root" imports that are included in JS bundle.
entry: paths.appIndexJs,
    output: {
        publicPath: "http://localhost:3000/", // Change this to the desired PORT

    },
    infrastructureLogging: {
        level: 'none',
    },
```

Same as Above:

```javascript


// Tools like Cloud9 rely on this.
const DEFAULT_PORT = parseInt(process.env.PORT, 10) || 3000;
const HOST = process.env.HOST || '0.0.0.0';

```