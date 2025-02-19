# Extensions
### Array
```swift
public extension Array {
    subscript(save index: Int) -> Element? {
        guard index >= 0, index < self.count else { return nil }
        return self[index]
    }
}
```

### Bundle
``` swift
public extension Bundle {
    var appName: String {
        object(forInfoDictionaryKey: "CFBundleName") as? String ?? "Unknown"
    }
    
    var appVersion: String {
        object(forInfoDictionaryKey: "CFBundleShortVersionString") as? String ?? "Unknown"
    }
}
```
