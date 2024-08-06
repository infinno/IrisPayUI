## Installation

### Swift Package Manager

The [Swift Package Manager](https://swift.org/package-manager/) is a tool for automating the distribution of Swift code and is integrated into the `swift` compiler. 

Once you have your Swift package set up, adding IrisPayUI as a dependency is as easy as adding it to the `dependencies` value of your `Package.swift`.

```swift
dependencies: [
    .package(url: "https://github.com/infinno/IrisPayUI.git", .upToNextMajor(from: "2.0.0"))
]
```

### Manual

1. Copy `IrisPayUI.xcframework` to your project’s folder. 
2. In the Project Navigator click on the project file and then click on the target you want to use `IrisPayUI` in.
3. Drag `IrisPayUI.xcframework` from Finder to the Frameworks, Libraries, and Embedded Content section.
4. In the Embed column choose Embed & Sign from the drop down, if it isn’t chosen already.
5. Build & Run the app.

## Documentation
You can Option+Click on the methods and properties to view documentation.

## Universal links support
Some banks (i.e. *Revolut*) have their own apps through which adding accounts and confirming payments is much easier than through a web browser. They can automatically return the user to your app by calling a predefined URL which your app must handle and tell our SDK to open it to complete the process. Here's what you have to do:

##### If you have your own IrisPay instance
1. Add the Associated Domains capability to your target and add `applinks:<your IrisPay instance domain>` to it.
2. Аdd an appropriately configured `apple-app-site-association` file to your instance.

##### If you use the default IrisPay instance
1. Provide us with your Developer Team ID and app Bundle Identifier so we can properly configure the `apple-app-site-association` file in the default IrisPay instance. 

When you've completed the above steps there's only one thing left to do: handle the URL in your App Delegate.
```swift
func application(_ application: UIApplication, continue userActivity: NSUserActivity, restorationHandler: @escaping ([UIUserActivityRestoring]?) -> Void) -> Bool {
    guard userActivity.activityType == NSUserActivityTypeBrowsingWeb,
          let incomingURL = userActivity.webpageURL
    else {
        return false
    }
    irisUI?.openRedirectedURL(incomingURL) // irisUI is a global instance of the IrisPayUI SDK
    return true
}
```
Or if you're using a Scene Delegate:
```swift
func scene(_ scene: UIScene, continue userActivity: NSUserActivity) {
    guard userActivity.activityType == NSUserActivityTypeBrowsingWeb,
          let incomingURL = userActivity.webpageURL
    else {
        return
    }
    irisUI?.openRedirectedURL(incomingURL) // irisUI is a global instance of the IrisPayUI SDK
}
```
The IrisPayUI SDK must open this URL or the process won't ever complete.

## Migration from 1.x to 2.0.0+
Xcode should provide FIXITs which should rename the old methods to their new names. If you need any help, please contact us.

## Requirements
- iOS 11+
