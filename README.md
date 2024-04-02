# text-to-speech-app

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### Debug with VSCode and Mozzila
ADD TO .vscode/launch.json

{
    "configurations": [
        {
            "name": "Vue:Client",
            "type": "firefox",
            "request": "launch",
            "url": "http://localhost:8080",
            "webRoot": "${workspaceFolder}/src",
            "pathMappings": [
                {
                    "url": "webpack://text-to-speech-app/src/components",
                    "path": "${workspaceFolder}/src/components"
                },
                {
                    "url": "file://",
                    "path": ""
                }
            ]
        }
    ]
}

