# Qiniu Cloud SDK for PHP
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)
[![CI](https://github.com/larva/qiniu-php-sdk/actions/workflows/test-ci.yml/badge.svg)](https://github.com/larva/qiniu-php-sdk/actions/workflows/test-ci.yml)
[![GitHub release](https://img.shields.io/github/v/tag/larva/qiniu-php-sdk.svg?label=release)](https://github.com/larva/qiniu-php-sdk/releases)
[![Latest Stable Version](https://img.shields.io/packagist/v/larva/qiniu-php-sdk.svg)](https://packagist.org/packages/larva/qiniu-php-sdk)
[![Total Downloads](https://img.shields.io/packagist/dt/larva/qiniu-php-sdk.svg)](https://packagist.org/packages/larva/qiniu-php-sdk)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/larva/qiniu-php-sdk/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/larva/qiniu-php-sdk/?branch=master)
[![Coverage Status](https://codecov.io/gh/larva/qiniu-php-sdk/branch/master/graph/badge.svg)](https://codecov.io/gh/larva/qiniu-php-sdk)
[![Join Chat](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/larva/qiniu-php-sdk?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![@qiniu on weibo](http://img.shields.io/badge/weibo-%40qiniutek-blue.svg)](http://weibo.com/qiniutek)


## 安装

推荐使用 `composer` 进行安装。可以使用 composer.json 声明依赖，或者运行下面的命令。SDK 包已经放到这里 [`larva/qiniu-php-sdk`][install-packagist] 。

```bash
$ composer require larva/qiniu-php-sdk
```

## 运行环境

- PHP **8.2+**
- 扩展依赖：`ext-curl`、`ext-xml`、`ext-json`

| Qiniu SDK 版本 | 最低 PHP 版本 |
|:--------------------:|:-----------------------------------------------:|
|          8.x         |                  8.2+                  |
|          7.x         | cURL extension,   5.3 - 5.6, 7.0 - 7.4, 8.0-8.1 |
|          6.x         |           cURL extension,   5.2 - 5.6           |

> 从 8.x 版本起，本 SDK 不再支持 PHP 8.1 及更早版本；生产环境建议使用 PHP 8.2 / 8.3 / 8.4。

## 主要依赖

- [`myclabs/php-enum`](https://packagist.org/packages/myclabs/php-enum) `^1.8.4`
- 开发依赖：[`phpunit/phpunit`](https://packagist.org/packages/phpunit/phpunit) `^10.5`、[`squizlabs/php_codesniffer`](https://packagist.org/packages/squizlabs/php_codesniffer) `^3.10`

## 使用方法

### 上传
```php
use Qiniu\Storage\UploadManager;
use Qiniu\Auth;
...
    $uploadMgr = new UploadManager();
    $auth = new Auth($accessKey, $secretKey);
    $token = $auth->uploadToken($bucket);
    list($ret, $error) = $uploadMgr->putFile($token, 'key', 'filePath');
...
```

## 测试

运行全部测试需要先配置七牛测试凭证环境变量：

```bash
$ export QINIU_ACCESS_KEY=<your-access-key>
$ export QINIU_SECRET_KEY=<your-secret-key>
$ export QINIU_TEST_BUCKET=<your-test-bucket>
$ export QINIU_TEST_DOMAIN=<your-test-domain>

$ composer install
$ ./vendor/bin/phpunit
```

代码风格检查：

```bash
$ ./vendor/bin/phpcs --standard=PSR2 src
```

## 常见问题

- `$error` 保留了请求响应的信息，失败情况下 `ret` 为 `none`, 将 `$error` 可以打印出来，提交给我们。
- API 的使用 demo 可以参考 [examples](https://github.com/larva/qiniu-php-sdk/tree/master/examples)。

## 代码贡献

详情参考[代码提交指南](https://github.com/larva/qiniu-php-sdk/blob/master/CONTRIBUTING.md)。

## 贡献记录

- [所有贡献者](https://github.com/larva/qiniu-php-sdk/contributors)

## 联系我们

- 如果需要帮助，请提交工单（在portal右侧点击咨询和建议提交工单，或者直接向 support@qiniu.com 发送邮件）
- 如果有什么问题，可以到问答社区提问，[问答社区](https://qiniu.segmentfault.com/)
- 更详细的文档，见[官方文档站](https://developer.qiniu.com/)
- 如果发现了 bug， 欢迎提交 [issue](https://github.com/larva/qiniu-php-sdk/issues)
- 如果有功能需求，欢迎提交 [issue](https://github.com/larva/qiniu-php-sdk/issues)
- 如果要提交代码，欢迎提交 pull request
- 欢迎关注我们的[微信](https://www.qiniu.com/#weixin) [微博](https://weibo.com/qiniutek)，及时获取动态信息。

## 代码许可

The MIT License (MIT).详情见 [License文件](https://github.com/larva/qiniu-php-sdk/blob/master/LICENSE).

[packagist]: https://packagist.org
[install-packagist]: https://packagist.org/packages/larva/qiniu-php-sdk
