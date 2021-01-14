---
title: "ssl이 적용된 워드프레스 로컬에서 ssl 비활성화 세팅"
slug: "Wordpress Local Force Ssl Deactive"
date: 2021-01-14T11:17:51+09:00
draft: false
---

## wp-config.php 에 세팅

```php

define('FORCE_SSL_LOGIN', false);
define('FORCE_SSL_ADMIN', false);

define('WP_HOME', 'http://localhost:8080');
define('WP_SITEURL', 'http://localhost:8080');

```

위 세팅 후 로그인해본다.
