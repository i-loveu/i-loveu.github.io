---
title: "Ios Swiftui Form"
date: 2021-07-09T16:26:01+09:00
draft: true
---

# SwiftUI Form

## view

### NavigationView

```swift
NavigationView {
    Form {
        Section(header: Text("Personal Information")) {
            TextField("First Name", text: $firstName)
            TextField("Last Name", text: $lastName)
            DatePicker("Birthdate", selection: $birthdate, displayedComponents: .date )
        }
    }
    .accentColor(.red)
}.navigationTitle("Account")
```

`.navigationTitle("Account")`

그뤂의 제목을 지정할 수 있다.

## input
