# CICD

[flutter官方推荐](https://flutter.cn/docs/deployment/cd)


## 将要用到的东西

- [fastlane](https://docs.fastlane.tools/) 是自动执行 iOS 和 Android 应用的 Beta 版部署和发布的最简单方法。 它可以处理所有繁琐的任务，例如生成屏幕截图、处理代码签名和发布应用程序。

## 无脑执行以下步骤

将 `com.tob.soulmate` 替换成具体的项目包名，然后`com.tob` 也是需要替换的。

### IOS

```bash
sudo gem install bundler -V  # 使用 Bundler 和 Gemfile 管理 fastlane 的依赖关系
```



由于您的 CI 机器将无法提示您输入双重身份验证或两步验证信息，您可以通过运行以下命令提前为您的 Apple ID 生成登录会话：

```bash
fastlane spaceauth -u user@email.com
```

然后，生成的值必须存储在 CI 系统上的 FASTLANE_SESSION 环境变量中。此会话将被重复使用，而不是每次 fastlane 与 Apple 的 API 通信时触发新的登录。


### Android

`keytool` 可能不在我们的系统路径中。它是 Java 的一部分，在安装 `Android Studio` 的时候会被一起安装。运行 `flutter doctor -v`，’Java binary at:’ 之后打印出来的就是它的路径，然后用 `java` 来替换以上命令中的 `keytool`，并加上 keytool 的完整路径即可。如果文件路径包含空格，类似 Program Files 这样的，请使用平台允许的命名规则。例如，在 Mac/Linux 上使用 Program\ Files，而在 Windows 上可以使用 "Program Files"。

```bash
/Applications/Android\ Studio.app/Contents/jbr/Contents/Home/bin/keytool -genkey -v -keystore upload-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias upload
```

生成的 `upload-keystore.jks` 文件后需要更新到 [android/key.properties](../android/key.properties)，其他 `storePassword` 和 `keyPassword` 都是你刚才输入的密码



## 参考
- [【devops】Flutter Github Actions - CI CD](https://www.bilibili.com/video/BV1DT411g7NJ/?vd_source=23c08322371e196164b48aafe7e60cf2)

- [Android 打包](https://www.cnblogs.com/gqx-html/p/14759889.html)

- [示例项目](https://github.com/swiftdo/flutter_best_practice)

- [GitHub Actions CI/CD for Flutter Fastlane (iOS) with possible mistakes](https://dev.to/subash_hungry/github-actions-cicd-for-flutter-fastlane-ios-with-possible-mistakes-pl0)