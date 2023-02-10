# 自己model 上传到GitHub 生成动态so库链接使用

## 使用到的两个网站

```
https://github.com/
https://jitpack.io/
```

# 第一步 

“这一步基本都会吧”

自己导成功一个model，新建一个空白项目，导入进去。然后整个项目上传到GitHub上面去，一定要提示成功后才能算真正的上传到了GitHub上面去了。

![第一步](https://user-images.githubusercontent.com/13359093/217768949-1806d945-2849-4e69-b46d-5cddf3669a61.png)

# 第二步

上传成功后点击项目，右边有个打包发布按钮，Create a new Releases

![2](https://user-images.githubusercontent.com/13359093/217769483-88e62c93-f919-45f3-b529-79dff06c0b2a.png)

进去后创建版本号和标题、说明的一些描述一定要进去设置一个动态链接的版本号，点击Publish releas发布即可，此时GitHub上面就已经发布成功了。

![4](https://user-images.githubusercontent.com/13359093/217770269-fa6ab21a-4fce-48a9-87f1-1b7f8c24dca8.png)

# 第三步

第二个网站 https://jitpack.io/ 点击进入然后用自己的git帐号再登录就会关联你所上传的项目，找到自己所上传的model项目

![9](https://user-images.githubusercontent.com/13359093/217771600-0abb23ca-2613-4999-91c9-87553fbd46ad.png)

然后点击Get it 找到对应的版本so库链接

![10](https://user-images.githubusercontent.com/13359093/217772113-052c34ff-52e0-4ea1-af0b-0a2aa9cb4626.png)

有过没报错底部就会出现对应的版本号，如果有报错之类的就不会出现有版本号，上面的log也会是红色的，就说明导成动态so库链接还有报错的地方，
就得一步一步去查，反之就用底部的链接放到自己开发的项目去引用就可以了

## 备注下
model 放到build gradle 里面的版本管理，最好使用统一引用版本号

```
ext {
    compileSdkVersion = 30
    minSdkVersion = 19
    targetSdkVersion = 27
    buildToolsVersion = "30.0.3"
    versionCode = 1
    versionName = "4.3.81"
    abiFilters = 'arm64-v8a'//'arm64-v8a', 'armeabi-v7a', 'x86', 'armeabi'
    arguments = "-DANDROID_STL=c++_shared"
    cppFlags = "-std=c++11"
    constraintLayoutVersion = '1.1.3'
}

```

然后再引用，这样有主意各个sdk版本的统一管理和一致；

```
  compileSdkVersion rootProject.ext.compileSdkVersion
  buildToolsVersion rootProject.ext.buildToolsVersion
  targetSdkVersion rootProject.ext.targetSdkVersion
    
```
