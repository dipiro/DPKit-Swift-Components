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
# ViewModifiers
```swift
struct OnLoadModifier: ViewModifier {
    @State private var didLoad = false
    
    private let action: (() -> Void)?
    
    // MARK: - Init
    init(perform action: (() -> Void)? = nil) {
        self.action = action
    }
    
    // MARK: - Body
    func body(content: Content) -> some View {
        content.onAppear {
            if didLoad == false {
                didLoad = true
                action?()
            }
        }
    }
}

// MARK: - Extension
extension View {
    public func onLoad(perform action: (() -> Void)? = nil) -> some View {
        modifier(OnLoadModifier(perform: action))
    }
}
```


