---
title: "워드프레스 관리자 에디터 커스텀 css 추가하기"
slug: "Wordpress Admin Editor Add Custom Css"
date: 2021-01-14T14:08:18+09:00
draft: false
---

## admin-editor-styles.css 만들기

theme/css/admin-editor-styles.css 위치에 파일 생성

```css
#tinymce {
  max-width: 860px;
}
```

## add_editor_style 추가

```php

// add custom css to editor
function wpdocs_theme_add_editor_styles()
{
  add_editor_style('admin-editor-styles.css');
}
add_action('admin_init', 'wpdocs_theme_add_editor_styles');

```
