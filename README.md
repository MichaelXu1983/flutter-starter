# Flutter 入门脚手架

## 目录简介

1. [介绍](#介绍) 
2. [前置知识](#前置知识) 
    - [Dart 语言](#Dart语言)
    - [对比其他框架异同](#对比其他框架异同)
    - [Flutter 运行机制](#Flutter运行机制)
3. [配置开发环境](#配置开发环境) 
    - [获取 Flutter SDK](#获取FlutterSDK)
    - [更新 Path 环境变量](#更新Path环境变量)
    - [下载并配置 Android Studio](#下载并配置AndroidStudio)
    - [安装并配置集成开发环境](#安装并配置集成开发环境)
    - [查看 Flutter 环境是否安装成功](#查看Flutter环境是否安装成功)
4. [开发步骤](#开发步骤) 
    - [创建初始化工程](#创建初始化工程)
    - [新建常用实践目录](#新建常用实践目录)
    - [Model 类定义](#Model类定义)
    - [全局变量 Global 类定义](#全局变量Global类定义)
    - [全局共享状态定义](#全局共享状态定义)
    - [网络请求封装](#网络请求封装)

## <a name="介绍">介绍</a>  

本项目是基于 flutter(1.12.13+hotfix.5) & Mac OS X(10.15.1) & Android SDK(29.0.1) 按照官方文档，遵循目前项目经验的常用实践，搭建的应用脚手架，不定期迭代新功能。大家可以直接克隆使用，也可以按照 README.md 一步一步自己搭建。

**Flutter 和 React Native 对比**  

|  | Flutter | React Native |
| --- | --- | --- |
| 开源时间 | 2017年 | 2015年 |
| 开发语言 | Dart | JavaScript |
| 技术架构 | 通过 JavaScript 桥与原生模块通信  | 使用内置模块，很少需要与原生模块通信 |
| 安装 | NPM | SDK |
| 项目配置 | 官网文档（官方中文翻译） | 官网文档（社区中文翻译） |
| UI 组件和 API | 主要通过社区 | 主要通过官方 |
| 社区支持 | 暂时领先 | 暂时落后 |
| 测试支持 | 主要由第三方支持 | 主要由官方支持 |
| 自动化构建和发布 | 通过第三方工具 | 除了第三方工具，还可以通过 CLI 工具 |
| 持续集成 | 通过第三方工具 | 除了第三方工具，还可以通过 CLI 工具 |


## <a name="前置知识">前置知识</a>  

### <a name="Dart语言">Dart 语言</a>  

[传送门](https://dart.dev/)

### <a name="对比其他框架异同">对比其他框架异同</a>  

[传送门](https://flutter.cn/docs/get-started/flutter-for/react-native-devs)

### <a name="Flutter运行机制">Flutter 运行机制</a>  

[传送门](https://book.flutterchina.club/chapter14/flutter_app_startup.html)

## <a name="搭建方法">搭建方法</a>
### <a name="获取FlutterSDK">获取 Flutter SDK</a>  
**Mac 系统** 
1. 下载 Flutter SDK
[传送门](https://storage.flutter-io.cn/flutter_infra/releases/stable/macos/flutter_macos_v1.12.13+hotfix.5-stable.zip)
> 要查看其他发行通道和以往的版本，请参阅 [SDK 版本列表](https://flutter.cn/docs/development/tools/sdk/releases) 页面  
2. 将文件解压到 `~/development` 下，确定 flutter bin 路径为 `~/development/flutter/bin` 

**Windowns 系统**  
1. 下载 Flutter SDK
[传送门](https://storage.flutter-io.cn/flutter_infra/releases/stable/windows/flutter_windows_v1.12.13+hotfix.5-stable.zip)
> 要查看其他发行通道和以往的版本，请参阅 [SDK 版本列表](https://flutter.cn/docs/development/tools/sdk/releases) 页面  
2. 将文件解压到 `C:\src\flutter` 下，确定 flutter bin 路径为 `C:\src\flutter\flutter\bin`  
3. 找到 `flutter` 目录中的 `flutter_console.bat` 文件，双击执行该批处理脚本

### <a name="更新Path环境变量">更新 Path 环境变量</a>  
**Mac 系统**  
```bash
vim ~/.bashrc   // 编辑你的默认 shell `rc` 文件，也有可能是 ~/.zshrc，
export PATH="$PATH:[PATH_TO_FLUTTER_BIN_DIRECTORY]" // 插入这一行，将其中的 [PATH_TO_FLUTTER_BIN_DIRECTORY] 更改为你 flutter bin 路径
source ~/.bashrc // 执行修改的 `rc` 文件，使其生效
```  

**Windowns 系统**
1. 在开始菜单的搜索功能键入 `env`，然后选择 **编辑当前用户的环境变量**
2. 在 **用户变量** 一栏中，检查是否有 **Path** 这个条目：
* 如果存在，直接把 `flutter\bin` 目录的完整路径以 `;` 作为分隔加到已有的值后面
* 如果不存在的话，在用户环境变量中创建一个新的 `Path` 变量，然后将 `flutter\bin` 所在的完整路径作为新变量的值  


### <a name="下载并配置AndroidStudio">下载并配置 Android Studio</a>  
1. 下载并安装 [Android Studio](https://developer.android.google.cn/studio)
2. 运行 Android Studio，并进入 "Android Studio Setup Wizard"，这会安装最新的 `Android SDK`，`Android SDK Platform-Tools` 以及 `Android SDK Build-Tools`，这些都是在开发 Android Flutter 应用时所需要的
3. 连接 Android 设备到开发机器上，并打开 `USB 调试` (详见 [安卓手机如何打开开发者选项USB调试](https://jingyan.baidu.com/article/f25ef2548d7941482c1b82f4.html))
> 至此你已经可以使用 Android Studio 进行 Flutter 开发了，但你也可以下载，你熟悉的其他集成开发环境，比如 IntelliJ IDEA 或者 VS Code 等，下面我以 VS Code 为例

### <a name="安装并配置集成开发环境">安装并配置集成开发环境</a>  
1. 下载 VS Code  [传送门](https://code.visualstudio.com/)
2. 安装 Flutter 和 Dart 插件  
* 打开 VS Code
* 打开 View > Command Palette
* 输入 `install Extensions`
* 在 `Extensions` 搜索输入框中输入 `flutter`，然后在列表中选择 Flutter 并单击安装（此过程中会自动安装必需的 Dart 插件）
* 点击 reload 以重新启动 VS Code  


### <a name="查看Flutter环境是否安装成功">查看 Flutter 环境是否安装成功</a>  
打开一个新的命令窗口，通过运行以下命令，来查看当前环境是否需要安装其他的依赖（如果想查看更详细的输出，增加一个 -v 参数即可）：
```bash
flutter doctor 

// Flutter 环境安装成功显示如下
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, v1.12.13+hotfix.5, on Mac OS X 10.15.1 19B88,
    locale zh-Hans-CN)

[✓] Android toolchain - develop for Android devices (Android SDK version 29.0.1)
[✓] Xcode - develop for iOS and macOS (Xcode 11.1)
[✓] Android Studio (version 3.4)
[✓] IntelliJ IDEA Ultimate Edition (version 2019.2.3)
[✓] VS Code (version 1.41.1)
[✓] Connected device (1 available)

• No issues found!
```  

## <a name="开发步骤">开发步骤</a>  

### <a name="创建初始化工程">创建初始化工程</a>  
1. 打开 View > Command Palette
2. 输入 `flutter`
3. 选择 `flutter:New Project` 
4. 输入项目名称 `github_client_app`
5. 选择项目存放路径
6. 等待项目自动初始化完成后，准备开发

### <a name="新建常用实践目录">新建常用实践目录</a>  
以下为本项目全部目录，在你的项目中新建没有的目录  

```
├── android
├── ios
├── docs   
│   ├── api.md              api 说明       
│   ├── contribute.md       共建指南     
│   ├── push-pr.md          如何提交 PR
│   ├── widget.md           widget 新增说明   
├── assets                  字体图片等资源
│   ├── fonts               字体
│   ├── i10n-arb            国际化
│   ├── imgs                图片
├── jsons                   Json 结构数据
├── lib
│   ├── common              工具类
│   ├── i10n                国际化相关的类
│   ├── models              Json 文件对应的 Dart Model 类
│   ├── routes              所有路由页面类
│   ├── states              保存 APP 中需要跨组件共享的状态类
│   ├── widgets             控件封装
│   ├── main.dart           入口
├── .gitignore              Git 忽略提交文件（切记要克隆和提交）
├── pubspec.lock            配置锁定文件（切记要克隆和提交）
├── pubspec.yaml            配置文件
├── README.md               自述文件
```  

### <a name="Model类定义">Model 类定义</a>  
#### 先梳理一下 APP 中将用到的数据，然后生成相应的 Dart Model 类   

**Github账号信息**  
登录 Github 后，我们需要获取当前登录者的 Github 账号信息，Github API 接口返回 Json 结构如下：  

```json
{
  "login": "octocat",
  "id": 1,
  "avatar_url": "https://github.com/images/error/octocat_happy.gif",
  "url": "https://api.github.com/users/octocat",
  "type": "User",
  "site_admin": false,
  "name": "monalisa octocat",
  "company": "GitHub",
  "blog": "https://github.com/blog",
  "location": "San Francisco",
  "email": "octocat@github.com",
  "hireable": false,
  "bio": "There once was...",
  "public_repos": 2,
  "public_gists": 1,
  "followers": 20,
  "following": 0,
  "created_at": "2008-01-14T04:33:35Z",
  "updated_at": "2008-01-14T04:33:35Z",
  "total_private_repos": 100,
  "owned_private_repos": 100
}
```
我们在 "jsons" 目录下创建一个 "user.json" 文件保存上述信息

**API缓存策略信息**  
由于Github服务器在国内访问速度较慢，我们对Github API应用一些简单的缓存策略。我们在“jsons”目录下创建一个“cacheConfig.json”文件缓存策略信息，定义如下：  

```json
{
  "enable":true, // 是否启用缓存
  "maxAge":1000, // 缓存的最长时间，单位（秒）
  "maxCount":100 // 最大缓存数
}
```  

**用户信息**  
用户信息(Profile)应包括如下信息：  
* Github账号信息；由于我们的APP可以切换账号登录，且登录后再次打开则不需要登录，所以我们需要对用户账号信息和登录状态进行持久化
* 应用使用配置信息；每一个用户都应有自己的APP配置信息，如主题、语言、以及数据缓存策略等
* 用户注销登录后，为了便于用户在退出APP前再次登录，我们需要记住上次登录的用户名

需要注意的是，目前 Github 有三种登录方式，分别是账号密码登录、oauth 授权登录、二次认证登录；这三种登录方式的安全性依次加强，但是在本项目中，为了简单起见，我们使用账号密码登录，因此我们需要保存用户的密码。  

> 注意：在这里需要提醒读者，在登录场景中，保护用户账号安全是一个非常重要且永恒的话题，在实际开发中应严格杜绝直接明文存储用户账密的行为

我们在“jsons”目录下创建一个“profile.json”文件，结构如下：  

```json
{
  "user":"$user", //Github账号信息，结构见"user.json"
  "token":"", // 登录用户的token(oauth)或密码
  "theme":5678, //主题色值
  "cache":"$cacheConfig", // 缓存策略信息，结构见"cacheConfig.json"
  "lastLogin":"", //最近一次的注销登录的用户名
  "locale":"" // APP语言信息
}
```  

**项目信息**  
由于APP主页要显示其所有项目信息，我们在“jsons”目录下创建一个“repo.json”文件保存项目信息。通过参考Github 获取项目信息的API文档，定义出最终的“repo.json”文件结构，如下：  

```json
{
  "id": 1296269,
  "name": "Hello-World",
  "full_name": "octocat/Hello-World",
  "owner": "$user",
  "parent":"$repo",
  "private": false,
  "html_url": "https://github.com/octocat/Hello-World",
  "description": "This your first repo!",
  "fork": false,
  "homepage": "https://github.com",
  "language": "JavaScript",
  "forks_count": 9,
  "stargazers_count": 80,
  "watchers_count": 80,
  "size": 108,
  "default_branch": "master",
  "open_issues_count": 0,
  "topics": [
    "octocat",
    "atom",
    "electron",
    "API"
  ],
  "has_issues": true,
  "has_projects": true,
  "has_wiki": true,
  "has_pages": false,
  "has_downloads": true,
  "pushed_at": "2011-01-26T19:06:43Z",
  "created_at": "2011-01-26T19:01:12Z",
  "updated_at": "2011-01-26T19:14:43Z",
  "permissions": {
    "admin": false,
    "push": false,
    "pull": true
  },
  "subscribers_count": 42,
  "license": {
    "key": "mit",
    "name": "MIT License",
    "spdx_id": "MIT",
    "url": "https://api.github.com/licenses/mit",
    "node_id": "MDc6TGljZW5zZW1pdA=="
  }
}
```  

#### 生成Dart Model类  

现在，我们需要的 Json 数据已经定义完毕，现在只需要运行 json_model package 提供的命令来通过 json 文件生成相应的 Dart 类：
1. 安装依赖

    ```yaml
    dev_dependencies: 
      json_model: #最新版本
      build_runner: ^1.0.0
      json_serializable: ^2.0.0
    ```  
2. 运行 `flutter packages pub run json_model` 命令生成Dart model类，生成的文件默认在 "lib/models" 目录下，使用时引用该目录的 index.dart 即可，第一次可能会失败出现下面错误：  

    ```bash
    Failed to precompile json_model:build_runner:
    Dart_LoadScriptFromKernel: The binary program does not contain 'main'.
    pub finished with exit code 1
    ```  
    此时只要再执行一次就可以了。  

### <a name="全局变量Global类定义">全局变量 Global 类定义</a>  
> 应用程序中通常会包含一些贯穿APP生命周期的变量信息，这些信息在APP大多数地方可能都会被用到，比如当前用户信息、Local信息等。在Flutter中我们把需要全局共享的信息分为两类：全局变量和共享状态。全局变量就是单纯指会贯穿整个APP生命周期的变量，用于单纯的保存一些信息，或者封装一些全局工具和方法的对象。而共享状态则是指哪些需要跨组件或跨路由共享的信息，这些信息通常也是全局变量，而共享状态和全局变量的不同在于前者发生改变时需要通知所有使用该状态的组件，而后者不需要。为此，我们将全局变量和共享状态分开单独管理。  

1. 安装依赖  

    ```yaml
    dependencies: 
      dio: ^3.0.3
      shared_preferences: ^0.5.1+1
      cached_network_image: ^0.8.0
    ```  
2. 新建网络缓存类  

    ```bash
    vim lib/common/net_cache.dart  // 内容详见对应文件
    ```  
3. 新建 GitHub API 类   

    ```bash
    vim lib/common/git_api.dart  // 内容详见对应文件
    ```  
4. 新建导出  

    ```bash
    vim lib/common/index.dart
    ...
    export 'git_api.dart';
    export 'global.dart';
    export 'net_cache.dart';
    ...
    
    vim lib/index.dart
    ...
    export 'models/index.dart';
    export 'common/index.dart';
    ...
    
    ```  
5. 新建 Global 类，它主要管理 APP 的全局变量，定义如下：  

    ```dart
    // 提供五套可选主题色
    const _themes = <MaterialColor>[
      Colors.blue,
      Colors.cyan,
      Colors.teal,
      Colors.green,
      Colors.red,
    ];
    
    class Global {
      static SharedPreferences _prefs;
      static Profile profile = Profile();
      // 网络缓存对象
      static NetCache netCache = NetCache();
    
      // 可选的主题列表
      static List<MaterialColor> get themes => _themes;
    
      // 是否为release版
      static bool get isRelease => bool.fromEnvironment("dart.vm.product");
    
      //初始化全局信息，会在APP启动时执行
      static Future init() async {
        _prefs = await SharedPreferences.getInstance();
        var _profile = _prefs.getString("profile");
        if (_profile != null) {
          try {
            profile = Profile.fromJson(jsonDecode(_profile));
          } catch (e) {
            print(e);
          }
        }
    
        // 如果没有缓存策略，设置默认缓存策略
        profile.cache = profile.cache ?? CacheConfig()
          ..enable = true
          ..maxAge = 3600
          ..maxCount = 100;
    
        //初始化网络请求相关配置
        Git.init();
      }
    
      // 持久化Profile信息
      static saveProfile() =>
          _prefs.setString("profile", jsonEncode(profile.toJson()));
    }
    ```  
6. 入口函数 lib/main.dart 中调用 Global 类 init 方法

    ```dart
    ...
    void main() async {
      WidgetsFlutterBinding
          .ensureInitialized(); // 此处调用是为了全局初始化 global.init(),参考：https://book.flutterchina.club/chapter14/flutter_app_startup.html
      await Global.init().then((e) {
        runApp(new MyApp());
      });
    }
    ...
    ```  

### <a name="全局共享状态定义">全局共享状态定义</a>   
使用 Provider 包来实现跨组件状态共享，因此我们需要定义相关的 Provider。在本项目中，需要共享的状态有登录用户信息、APP主题信息、APP语言信息。由于这些信息改变后都要立即通知其它依赖的该信息的 Widget 更新，所以我们应该使用 ChangeNotifierProvider，另外，这些信息改变后都是需要更新 Profile 信息并进行持久化的。  
1. 安装依赖  

    ```yaml
    dependencies: 
      provider: ^3.0.0+1
    ```  
2. 更新导出  

    ```bash
    vim lib/index.dart
    ...
    export 'package:provider/provider.dart';
    export 'package:flutter/material.dart';
    ...
    
    ```  
3. 定义一个 ProfileChangeNotifier 基类(lib/states/profile_change_notifier.dart)，然后让需要共享的 Model 继承自该类即可，ProfileChangeNotifier 定义如下：

    ```dart
    class ProfileChangeNotifier extends ChangeNotifier {
      Profile get _profile => Global.profile;
    
      @override
      void notifyListeners() {
        Global.saveProfile(); //保存Profile变更
        super.notifyListeners(); //通知依赖的Widget更新
      }
    }
    
    // 用户状态(用户状态在登录状态发生变化时更新、通知其依赖项)
    class UserModel extends ProfileChangeNotifier {
      User get user => _profile.user;
    
      // APP是否登录(如果有用户信息，则证明登录过)
      bool get isLogin => user != null;
    
      //用户信息发生变化，更新用户信息并通知依赖它的子孙Widgets更新
      set user(User user) {
        if (user?.login != _profile.user?.login) {
          _profile.lastLogin = _profile.user?.login;
          _profile.user = user;
          notifyListeners();
        }
      }
    }
    
    // APP主题状态(主题状态在用户更换APP主题时更新、通知其依赖项)
    class ThemeModel extends ProfileChangeNotifier {
      // 获取当前主题，如果为设置主题，则默认使用蓝色主题
      ColorSwatch get theme => Global.themes
          .firstWhere((e) => e.value == _profile.theme, orElse: () => Colors.blue);
    
      // 主题改变后，通知其依赖项，新主题会立即生效
      set theme(ColorSwatch color) {
        if (color != theme) {
          _profile.theme = color[500].value;
          notifyListeners();
        }
      }
    }
    
    // APP语言状态(当APP语言选为跟随系统（Auto）时，在系通语言改变时，APP语言会更新；当用户在APP中选定了具体语言时（美国英语或中文简体），则APP便会一直使用用户选定的语言，不会再随系统语言而变)
    class LocaleModel extends ProfileChangeNotifier {
      // 获取当前用户的APP语言配置Locale类，如果为null，则语言跟随系统语言
      Locale getLocale() {
        if (_profile.locale == null) return null;
        var t = _profile.locale.split("_");
        return Locale(t[0], t[1]);
      }
    
      // 获取当前Locale的字符串表示
      String get locale => _profile.locale;
    
      // 用户改变APP语言后，通知依赖项更新，新语言会立即生效
      set locale(String locale) {
        if (locale != _profile.locale) {
          _profile.locale = locale;
          notifyListeners();
        }
      }
    }
    ```  
4. 新建导出

    ```bash
    vim lib/states/index.dart
    ...
    export 'profile_change_notifier.dart';
    ...
    ```  

### <a name="网络请求封装">网络请求封装</a>   
**网络接口缓存**  
> 由于在国内访问Github服务器速度较慢，所以我们应用一些简单的缓存策略：将请求的url作为key，对请求的返回值在一个指定时间段类进行缓存，另外设置一个最大缓存数，当超过最大缓存数后移除最早的一条缓存。但是也得提供一种针对特定接口或请求决定是否启用缓存的机制，这种机制可以指定哪些接口或那次请求不应用缓存，这种机制是很有必要的，比如登录接口就不应该缓存，又比如用户在下拉刷新时就不应该再应用缓存  

1. 定义保存缓存信息的 `CacheObject` 类（详见对应文件 `lib/common/net_cache.dart`）  
2. 实现具体的缓存策略，由于我们使用的是 dio package，所以我们可以直接通过拦截器来实现缓存策略，定义 `NetCache` 类（详见对应文件 `lib/common/net_cache.dart`）  

**封装网络请求**  
一个完整的APP，可能会涉及很多网络请求，为了便于管理、收敛请求入口，工程上最好的作法就是将所有网络请求放到同一个源码文件中。由于我们的接口都是请求的Github 开发平台提供的API，所以我们定义一个Git类，专门用于Github API接口调用。另外，在调试过程中，我们通常需要一些工具来查看网络请求、响应报文，使用网络代理工具来调试网络数据问题是主流方式。配置代理需要在应用中指定代理服务器的地址和端口，另外Github API是HTTPS协议，所以在配置完代理后还应该禁用证书校验，这些配置我们在Git类初始化时执行（init()方法）。

详见对应文件 `lib/common/git_api.dart`  

可以看到我们在init()方法中，我们判断了是否是调试环境，然后做了一些针对调试环境的网络配置（设置代理和禁用证书校验）。而Git.init()方法是应用启动时被调用的（Global.init()方法中会调用Git.init()）。  

另外需要注意，我们所有的网络请求是通过同一个dio实例（静态变量）发出的，在创建该dio实例时我们将Github API的基地址和API支持的Header进行了全局配置，这样所有通过该dio实例发出的请求都会默认使用者些配置。  

在本项目中，只用到了登录接口和获取用户项目的接口，所以在Git类中只定义了login(…)和getRepos(…)方法，如果要在本项目的基础上扩充功能，可以将其它的接口请求方法添加到Git类中，这样便实现了网络请求接口在代码层面的集中管理和维护。 
