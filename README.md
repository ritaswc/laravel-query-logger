### 修改自 https://github.com/overtrue/laravel-query-logger

A dev tool to log all queries for Laravel applications.

## 支持版本

| Laravel | PHP |
|---|---|
| 5.5 – 13 | 7.4 – 8.5 |

> Laravel 12 / 13 与 PHP 8.5 已纳入支持范围。

## 安装

```bash
composer require ritaswc/laravel-query-logger --dev
```

## 配置

在 `config/logging.php` 的 `channels` 中增加：

```php
'query' => [
    'driver' => 'daily',
    'path'   => storage_path('logs/query.log'),
    'level'  => 'debug',
    'days'   => 7,
],
```

并开启：

```php
'query' => [
    'enabled'     => env('LOG_QUERY', false),
    'channel'     => 'query',
    'slower_than' => 0,
    'only_prefix' => '',
    'trigger'     => '',
],
```

`trigger` 支持环境变量、请求 Header、Query 参数或 Cookie；配置后只有带该标记的请求才会记录 SQL。
