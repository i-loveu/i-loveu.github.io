---
title: "워드프레스 페이지네이션 번호를 가지고 상세와 리스트를 옮겨가기"
slug: "Wordpress Single Page to List With Page Number"
date: 2021-01-14T09:27:09+09:00
draft: false
---

## list page

```php
$paged = (get_query_var('paged')) ? get_query_var('paged') : 1;
echo '<a href="' . get_permalink() . '&paged=' . $paged . '">';
```

## single page

```php
global $paged;
echo '<a href="' . home_url('/') . $post_type . '?page=' . $paged . '" class="btn_01 btn_list">목록으로</a>';
```

리스트페이지에서는 /page/2 이런 식으로 되어 있지만, parameter를 넘길 때에는 ?page 로 넘겨야 한다.
