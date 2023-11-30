# flutter_starter
flutter_starter

替换所有 `flutter_starter` 成你的项目名，还有文件名内包含`flutter_starter`的

将 `com.tob.soulmate` 替换成具体的项目包名，然后`com.tob` 也是需要替换的。

## Getting Started

logo 变更后需要运行，[详细了解](https://github.dev/fluttercommunity/flutter_launcher_icons/tree/master/example/flavors)

```bash
flutter pub run flutter_launcher_icons
```

### ios

这里一共是两个版本的app，分别是 `dev` 和 `prod`, 留意 [ios/fastlane/Fastfile](./ios/fastlane/Fastfile) 文件。注意替换 `app_identifier` 的值。

需要在 [identifiers](https://developer.apple.com/account/resources/identifiers/list) 上建立对应的identifier，然后替换 `app_identifier` 的值

本地构建

```bash
cd ios
bundle exec fastlane ios dev_test
bundle exec fastlane ios dev_store
```

生产构建

```bash
cd ios
bundle exec fastlane ios prod_test
bundle exec fastlane ios prod_store
```

截图

```bash
cd ios
fastlane screenshots  # 截图 并上传
fastlane release # 发布
```

需要设置的环境变量

```bash
APP_STORE_CONNECT_API_KEY_ISSUER_ID
APP_STORE_CONNECT_API_KEY_KEY # .p8 密钥的内容
APP_STORE_CONNECT_API_KEY_KEY_ID
MATCH_GIT_PRIVATE_KEY # match 时的 git 仓库的请求token
MATCH_KEYCHAIN_PASSWORD # 运行 fastlane match development | appstore 时输入过的密码
MATCH_PASSWORD # 运行 fastlane match development | appstore 时输入过的密码
```

[获取APP_STORE_CONNECT_API_KEY](https://appstoreconnect.apple.com/access/api)

[获取 MATCH_GIT_PRIVATE_KEY](https://github.com/settings/tokens)

## 常见问题

- [解决gem安装慢或卡住](https://juejin.cn/post/6987549601343471623)