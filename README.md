# 部署 Flyio 試作

Heroku 快不能用了，所以逃難到多人推薦的平台上


[Fly.io](https://fly.io/)

使用在本機產生 docker imager 後推送去至平台上的方式部署


以下使用 Vite 產生專案來試作

---

### 撰寫 Dockerfile
撰寫執行專案的 docker image
此步驟也可跳過讓 flyctl 自行判斷

```
FROM pierrezemb/gostatic
COPY ./dist/ /srv/http/
```

### fly.io 指令
#### 登入 fly.io
開始後面的部署流程

```
flyctl auto login
```

#### 啟動 flyctl
會有一串的互動操作

例如： App 名稱、部署的位置之類的

```
flyctl launch
```

再來需要修改預設的 internal_port,

因為使用的 goStatic image 所預設監聽的 port 是 8043

如果是部署 Laravel 則需設定為 8000

```
internal_port = 8080  =>  internal_port = 8043
```

### 部署

指令為：

```
flyctl deploy
```

完成之後, `open` 的指令可開啟部署的站台

```
flyctl open
```
---



#### 參考
[【 Cloud 】部署 React App 到 Fly.io 雲端平台](https://learningsky.io/deploy-react-docker-container-app-to-flyio-cloud/)

[fly.io Docs](https://fly.io/docs/)