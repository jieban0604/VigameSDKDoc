# 产品参数配置
## 4.1 配置产品参数  

测试时可按照demo中的参数进行配置，正式上线前由出包方替换正式参数。

```
<meta-data
    android:name="com.vigame.sdk.appid"
    android:value="10001" />
<meta-data
    android:name="com.vigame.sdk.appkey"
    android:value="abcdefgh" />
<meta-data
    android:name="com.vigame.sdk.prjid"
    android:value="10001" />
<meta-data
    android:name="com.vigame.sdk.channel"
    android:value="${WB_CHANNEL}" />
```

## 4.2 配置游戏   
通过assets文件夹中的ConfigVigame.xml进行配置，属性说明如下：  

| 名称               | 解释                         | 是否必须 |
| ------------------ | ---------------------------- | -------- |
| GameOpenActivity   | 闪屏后进入的Activity路径名称 | 是       |
| ScreenOrientation  | 屏幕方向                     | 是       |
| SupportAdPositions | 支持的广告位名称             | 否       |
| SplashFile         | 默认的闪屏文件（assets中）   | 否       |
| WithSplashAD       | 是否出现闪屏广告（默认出现） | 否       |

## 
