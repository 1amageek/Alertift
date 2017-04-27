# Alertift
UIAlertControlelr wrapper for Swift

[![GitHub release](https://img.shields.io/github/release/sgr-ksmt/Alertift.svg)](https://github.com/sgr-ksmt/Alertift/releases)
![Language](https://img.shields.io/badge/language-Swift%203-orange.svg)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![CocoaPods](https://img.shields.io/badge/Cocoa%20Pods-✓-4BC51D.svg?style=flat)](https://cocoapods.org/pods/Alertift)
[![CocoaPodsDL](https://img.shields.io/cocoapods/dt/Alertift.svg)](https://cocoapods.org/pods/Alertift)
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/matteocrippa/awesome-swift#ui)  


```swift
Alertift.alert(title: "Confirm", message: "Delete this post?")
    .action(.destructive("Delete")) {
        // delete post
    }
    .action(.cancel("Cancel"))
    .show()
```

![img1](Documents/img1.png)

## Feature
- Method chain
- UITextField support
- iPad support(Action Sheet, popover)

## Examples

### Simple Alert

```swift
Alertift.alert(title: "Sample 1", message: "Simple alert!")
    .action(.default("OK"))
    .show()
```

![img2](Documents/img2.png)


```swift
Alertift.alert(title: "Confirm", message: "Delete this post?")
    .action(.destructive("Delete")) {
        // delete post
    }
    .action(.cancel("Cancel"))
    .show()
```

![img1](Documents/img1.png)


### Prompt Alert

```swift
Alertift.alert(title: "Sign in", message: "Input your ID and Password")
    .textField { textField in
        textField.placeholder = "ID"
    }
    .textField { textField in
        textField.placeholder = "Password"
        textField.isSecureTextEntry = true
    }
    .action(.cancel("Cancel"))
    .action(.default("Sign in"), textFieldsHandler: { textFields in
        let id = textFields?.first?.text ?? ""
        let password = textFields?.last?.text ?? ""
        // sign in
    })
    .show()
```

![img3](Documents/img3.png)

### Action Sheet

```swift
Alertift.actionSheet(message: "Which food do you like?")
   .action(.default("🍣"))
   .action(.default("🍎"))
   .action(.default("🍖"))
   .action(.default("🍅"))
   .action(.cancel("None of them"))
   .finally { action, index in
       if action.style == .cancel {
           return
       }
       Alertift.alert(message: "\(index). \(action.title!)")
           .action(.default("OK"))
           .show()
   }
   .show()
```

![img4](Documents/img4.png)

#### for iPad
Use `popover(sourceView:SourceRect)`

```swift
Alertift.actionSheet(message: "Which food do you like?")
   .popover(sourceView: self.view, sourceRect: button.frame)
   .action(.default("🍣"))
   .action(.default("🍎"))
   .action(.default("🍖"))
   .action(.default("🍅"))
   .action(.cancel("None of them"))
   .finally(handler: { action, index in
       if action.style == .cancel {
           return
       }
       Alertift.alert(message: "\(index). \(action.title!)")
           .action(.default("OK"))
           .show()
   })
   .show()
```

![img5](Documents/img5.png)


## Requirements
- iOS 9.0+
- Xcode 8.1+
- Swift 3.0+

## Installation

### Carthage

- Add the following to your *Cartfile*:

```bash
github "sgr-ksmt/Alertift" ~> 1.0
```

- Run `carthage update`
- Add the framework as described.
<br> Details: [Carthage Readme](https://github.com/Carthage/Carthage#adding-frameworks-to-an-application)


### CocoaPods

**Alertift** is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'Alertift', '~> 1.0'
```

and run `pod install`

### Manually Install
Download all `*.swift` files and put your project.

## Change log
Change log is [here](https://github.com/sgr-ksmt/Alertift/blob/master/CHANGELOG.md).

## Communication
- If you found a bug, open an issue.
- If you have a feature request, open an issue.
- If you want to contribute, submit a pull request.:muscle:

## License

**Alertift** is under MIT license. See the [LICENSE](LICENSE) file for more info.
