# 如何对不同的 URL 强制使用 HTTPS 或者 HTTP

您能在您的网站领域安全配置强制使用 HTTPS 协议。您可以强迫您的站点在安全配置中使用 HTTPS 协议。这是通过 **access_control** 规则使用 **requires_channel** 选项来完成的。例如，如果您想强制所有的 URL 以 **/secure** 开始来使用 HTTPS，那么你可以使用以下配置：

YAML：

```
access_control:
    - { path: ^/secure, roles: ROLE_ADMIN, requires_channel: https }
```

XML:

```
<access-control>
    <rule path="^/secure" role="ROLE_ADMIN" requires_channel="https" />
</access-control>
```

PHP：

```
'access_control' => array(
    array(
        'path'             => '^/secure',
        'role'             => 'ROLE_ADMIN',
        'requires_channel' => 'https',
    ),
),
```

登录表单本身就需要允许匿名访问，否则用户将无法进行身份验证。强制它使用 HTTPS，你仍然可以通过使用 **is_authenticated_anonymously** 选项使用 **access_control** 规则：

YAML:

```
access_control:
    - { path: ^/login, roles: IS_AUTHENTICATED_ANONYMOUSLY, requires_channel: https }
```

XML:

```
<access-control>
    <rule path="^/login"
          role="IS_AUTHENTICATED_ANONYMOUSLY"
          requires_channel="https" />
</access-control>
```

PHP:

```
'access_control' => array(
    array(
        'path'             => '^/login',
        'role'             => 'IS_AUTHENTICATED_ANONYMOUSLY',
        'requires_channel' => 'https',
    ),
),
```

它也可以指定在路径配置中使用 HTTPS，浏览[如何强制路径始终使用 HTTPS 或 HTTP](http://symfony.com/doc/current/cookbook/routing/scheme.html) 了解更多细节。
