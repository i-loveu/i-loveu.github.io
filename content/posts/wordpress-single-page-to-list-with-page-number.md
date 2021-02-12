---
title: "워드프레스 페이지네이션 번호를 가지고 상세와 리스트를 옮겨가기"
slug: "Wordpress Single Page to List With Page Number"
date: 2021-01-14T09:27:09+09:00
draft: false
---

## list page

```php
$paged = (get_query_var('paged')) ? get_query_var('paged') : 1;
echo '<a href="' . get_permalink() . '&paging=' . $paged . '">';
```

리스트에서 &page= 나 &paged= 로 넘길경우 예약된 파라메터로 삭제될 수 있는데, 임시 paging 파라메터로 넘긴다

## single page

```php
$paged = 1;
if ($_GET['paging']) {
  $paged = $_GET['paging'];
}
echo '<a href="' . home_url('/') . $post_type . '?paged=' . $paged . '" >목록으로</a>';
```

리스트페이지에서는 /page/2 이런 식으로 되어 있지만, parameter를 넘길 때에는 &paged= 로 넘겨야 한다.
