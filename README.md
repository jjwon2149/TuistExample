# Tuist Practice Project (UIKit)

This repository is for practicing [Tuist](https://tuist.io/) with a focus on generating a basic iOS project using UIKit. Follow the steps below to install Tuist and set up the project.

## Installation

If version pinning across environments is not a concern, you can install Tuist using Homebrew and our formulas:

```bash
brew tap tuist/tuist
brew install --formula tuist
brew install --formula tuist@x.y.z
```



## Getting Started
새로만든 디렉토리로 이동하여
```bash
tuist init --platform ios
```

generate, xcode 실행 (기본은 SwiftUI로 generate 해줌.)
```bash
tuist generate  
```

## UIKit으로 실행하는법
Source 디렉토리에 기본으로 생성되는 파일 삭제. (ContentView.swift, "Root 디렉토리 이름"App.swift)

Source 디렉토리에 AppDelegate.swift 생성
```swift
import UIKit

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    var window: UIWindow?

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        window = UIWindow(frame: UIScreen.main.bounds)
        let viewController = ViewController()  
        window?.rootViewController = viewController
        window?.makeKeyAndVisible()

        return true
    }
}
```

Source 디렉토리에 ViewController.swift 생성
```swift
import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        
        view.backgroundColor = .white

        let label = UILabel()
        label.text = "Hello, Tuist!"
        label.font = UIFont.systemFont(ofSize: 24)
        label.textColor = .black
        label.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(label)

        NSLayoutConstraint.activate([
            label.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            label.centerYAnchor.constraint(equalTo: view.centerYAnchor)
        ])
    }
}
```

이후 
```bash
tuist generate
```

## 의존 그래프 그리기
```bash
tuist graph
```