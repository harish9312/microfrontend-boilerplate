## Start editing the /config/webpack.config.js line 

- Edit the below content to expose the Component and Remote the same

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