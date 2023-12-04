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

安装依赖

```bash
gem install bundler
gem install fastlane
flutter pub get
```

构建 dev 版本

```bash
cd ios
bundle exec fastlane ios dev_test # 构建并上传到 testFlight
bundle exec fastlane ios dev_store # 构建并上传到 app store
```

构建 prod 版本

```bash
cd ios
bundle exec fastlane ios prod_test # 构建并上传到 testFlight
bundle exec fastlane ios prod_store # 构建并上传到 app store
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
MATCH_GIT_PRIVATE_KEY # match 时的 git 仓库的请求token，如果你已经有权限这个不需要，在cicd的环境需要
MATCH_KEYCHAIN_PASSWORD # 运行 fastlane match development | appstore 时输入过的密码
MATCH_PASSWORD # 运行 fastlane match development | appstore 时输入过的密码
```

[获取APP_STORE_CONNECT_API_KEY](https://appstoreconnect.apple.com/access/api)

[获取 MATCH_GIT_PRIVATE_KEY](https://github.com/settings/tokens)

注意 配置的 [ios/fastlane/Matchfile](./ios/fastlane/Matchfile) 中 `git_url` 是 `https` 还是 `git`。

`git` 的话需要使用 `MATCH_GIT_BASIC_AUTHORIZATION`

`MATCH_GIT_BASIC_AUTHORIZATION` 的获取方式

```bash
echo -n your_github_username:your_personal_access_token | base64
```

`https` 的话需要使用 `MATCH_GIT_PRIVATE_KEY`

### android

```bash
flutter build appbundle --flavor=dev
flutter build appbundle --flavor=prod
```


## 常见问题

- [解决gem安装慢或卡住](https://juejin.cn/post/6987549601343471623)