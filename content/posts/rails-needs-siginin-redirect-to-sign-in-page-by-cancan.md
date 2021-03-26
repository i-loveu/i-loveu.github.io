---
title: "Rails 로그인이 필요한 페이지 로그인 갔다 돌아오는 방법 by Cancan Gem"
slug: "Rails Needs Siginin Redirect to Sign in Page by Cancan"
categories: ["rubyonrails"]
tags: ["rubyonrails", "ruby", "cancan"]
date: 2021-03-26T17:00:51+09:00
draft: false
---

## application_controller.rb 코드 추가 

application_controller.rb에 아래 사항 추가 

```ruby
class ApplicationController < ActionController::Base
    rescue_from CanCan::AccessDenied, with: :access_denied
    private

    def access_denied(exception)
    store_location_for :user, request.path
    redirect_to user_signed_in? ? root_path : new_user_session_path, alert: exception.message
    end
end
```