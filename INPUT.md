# 接入方法
## 1.1导入SDK
### 1.1.1分别拷贝assets和libs,jniLibs目录下的内容到工程的同名目录  
### 1.1.2在应用的build.gradle中添加如下引用：


```
repositories {
    flatDir {
        dirs 'libs'//project(':app').file('libs')
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    //基础模块
    compile 'com.android.support:support-v4:26.+'
    compile(name: 'libGCOffers-release', ext: 'aar')
    compile(name: 'libPushService-release', ext: 'aar')
    //百度广告（仅供测试）
    //compile(name: 'libAD_Baidu-release', ext: 'aar')
    //支付宝支付（仅供测试）
    //compile(name: 'libPayExt_AliPay-release', ext: 'aar')
    //compile(name: 'AliPayApp-release', ext: 'aar')
}
```

## 1.2修改Manifest文件  


```
<meta-data
    android:name="com.vigame.sdk.appid"
    android:value="10001" />
<meta-data
    android:name="com.vigame.sdk.appkey"
    android:value="abcdefg" />
<meta-data
    android:name="com.vigame.sdk.prjid"
    android:value="10001" />
<meta-data
    android:name="com.vigame.purchase.channel"
    android:value="${WB_CHANNEL}" />

<activity android:name="com.libVigame.VigameStartActivity"
    android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```
注意，此时启动的Activity已经是VigameStartActivity。请通过assets/ConfigVigame.xml设置启动的Activity。

## 1.3添加JAVA调用代码
### 1.3.1修改应用的Application，在以下生命周期加入调用代码。

```
public class MyApplication extends Application {
    protected void attachBaseContext(Context base) {
        super.attachBaseContext(base);
        VigameLoader.applicationAttachBaseContext(this, base);
    }

    public void onCreate() {
        super.onCreate();
        VigameLoader.applicationOnCreate(this);
    }

}
```
### 1.3.2修改应用的主Activity，将以下代码加入到主Activity对应的生命周期中。

```
    VigameLoader.activityOnCreate(this);
    VigameLoader.activityOnDestroy(this);
    VigameLoader.activityOnResume(this);
    VigameLoader.activityOnPause(this);
    VigameLoader.activityOnWindowFocusChanged(this,hasFocus);
    VigameLoader.activityOnActivityResult(this, requestCode, resultCode, data);
    VigameLoader.activityOnRestart(this);
```

