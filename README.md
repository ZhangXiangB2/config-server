# config-server

## 部署
- 於 application.properties 中設定相關參數後，透過 Spring Boot Application 直接啟動

```
此處使用 git 且使用 private repository 實作，實際上可以放置於 Local，或是 git public repository
spring.cloud.config.server.git.uri=https://github.com/ZhangXiangB2/ConfigServerSetting.git
spring.cloud.config.server.git.username=b25459870@gmail.com
spring.cloud.config.server.git.password=***********
```
### 測試

```
可以取得檔名為 config-client-prod.properties 中於且 branch 為 master 的設定檔
Get http://localhost:8888/config-client/prod/master
```

```
application.properties encrypt.key=test
可以得到 post body text 中字串使用 test 去加密的結果

curl -X POST \
  http://localhost:8888/encrypt \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 4dac2c7e-8409-9e8b-8837-09cedfd5ce86' \
  -d testencrypt
```

```
application.properties encrypt.key=test
將 encrypt 結果攜帶於 post body text 可以得到使用 test 解密的結果 

curl -X POST \
  http://127.0.0.1:8888/decrypt \
  -H 'cache-control: no-cache' \
  -H 'postman-token: e23b7a2b-f467-1132-2c81-a24f312466e5' \
  -d 3c879cae8f7127a2f3dc2e5fd799795b515dca2055659b1d8d1cae1c53f145b3
```
