changes I made to run correctly on nvm>18 below

[version]
```
nvm use 14.8.0
```

[package.json] 
* had issue with openssl when trying to >npm run serve; adding this fixes it. 
```
"serve": "export NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service serve --host localhost --port 8080",
```

[vue.config.js]
 * adding this enables hot reload, ignoring node_modules increases hot relaod speed
```
module.exports = {
  configureWebpack: {
    devServer: {
      watchOptions: {
        poll: true,
        ignored: /node_modules/
      }
    }
  },
  ...
}
  ```



## cloned\/
#### Copyright &copy; 2020 [Darian Nocera](https://www.darnocer.io)
