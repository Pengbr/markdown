用electron开发电脑桌面端应用

```js
let electron = require('electron')

let app = electron.app
let BrowerWindow = electron.BrowserWindow

let mainWindow = null

app.on('ready', () => {
    mainWindow = new BrowerWindow({ width: 800, height: 800 })
    mainWindow.loadFile('index.html')
    mainWindow.on('close', () => {
        mainWindow = null
    })
})
```

