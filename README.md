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

本地构建

```bash
bundle exec fastlane ios build
```

生产构建

```bash
bundle exec fastlane ios build flavor:prod
```

截图

```bash
cd ios
fastlane screenshots  # 截图 并上传
fastlane release # 发布
```

## 常见问题

- [解决gem安装慢或卡住](https://juejin.cn/post/6987549601343471623)