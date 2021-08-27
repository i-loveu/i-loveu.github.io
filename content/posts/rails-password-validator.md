---
title: "Rails 특수문자 Password Validator"
slug: "Rails Password Validator"
date: 2021-06-09T22:46:27+09:00
draft: false
---

## Rails 특수문자 Password Validator

```ruby
def password_special_char
    special = "?<>',?[]}{=-)(*&^%$#`~{}!"
    regex = /[#{special.gsub(/./){|char| "\\#{char}"}}]/
    return if password =~ regex
    errors.add :password, '영문, 숫자, 특수문자 조합 10자 이상 비밀번호를 입력해주세요.'
end
```
