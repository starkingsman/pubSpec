## H5上报用户事件到原生端 

### 上报到Android
<name>.postMessage(<messageBody>)

### 上报到iOS
window.webkit.messageHandlers.<name>.postMessage(<messageBody>)

name为自定义的方法名: 比如
#### "afEvent" 

messageBody为传参，需要借助postMessage进行传递
格式:

 ## eventName: login(登入) / signup(注册)
 data: {object}
 *  - eventName: {string}

 ## firstDeposit(首充) / 复充(secondDeposit)
  data: {object}
 *  - eventName: {string}
 *  - eventValue: {object}
 *      - isFirstDeposit: {bool}
 *      - amount: {number|string}


范例:
## login(登入) / signup(注册)
```sh
jsonData = {
    eventName: "login"
}
```
## firstDeposit(首充) 
```sh
jsonData = {
    eventName: "firstDeposit",
    eventValue: {
        isFirstDeposit: true,
        amount: 100
    }
}
```
## 复充(secondDeposit)
```sh
jsonData = {
    eventName: "secondDeposit",
    eventValue: {
        isFirstDeposit: false,
        amount: 200
    }
}
```

jsonData序列化成string

### Android
afEvent.postMessage(jsonData)

### iOS
window?.webkit?.messageHandlers.afEvent.postMessage(jsonData)





