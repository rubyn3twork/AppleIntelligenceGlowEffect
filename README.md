# Apple Intelligence Glow Effect

A beautiful, customizable SwiftUI-based glow effect that mimics Apple's Intelligence UI design language. This effect is built entirely in SwiftUI without Metal shaders, making it lightweight and easy to implement across Apple platforms.

![Header](ReadMe/Header.png)

## Features

- 🌟 Pure SwiftUI implementation - no Metal shaders required
- 📱 Cross-platform support for Apple devices
- 🎨 Fully customizable colors and animations
- ⚡️ Optimized performance with configurable parameters
- 🔄 Smooth, fluid animations
- 🎯 Easy to integrate into existing projects

## Platform Support

- ✅ WatchOS (Complete)
- ✅ iOS (Complete)
- ⏳ iPadOS (Coming Soon)
- ⏳ macOS (Coming Soon)

## Demos

### WatchOS
Two versions available:
- `WatchOS.swift`: Original version (Series 10 compatible)
- `WatchOS_WithFreeze.swift`: Enhanced version with freeze capability and full WatchOS 11 compatibility

![WatchOS Demo](ReadMe/WatchOSDemo.gif)

### iOS
Two stunning effects:
1. Type to Siri Effect
2. Apple Intelligence Glow Effect

![IOS Type To Siri Effect](ReadMe/TypeToSiri.gif)
![IOS Demo](ReadMe/IphoneDemo.gif)

## Installation

1. Copy the desired platform file (e.g., `WatchOS.swift` or `IOS.swift`) into your project
2. Import the file in your SwiftUI view
3. Implement the effect as shown in the examples below

## Customization Guide

### 1. Animation Timing
Adjust the animation speed and interval to match your needs:

```swift
Timer.scheduledTimer(withTimeInterval: 0.25, repeats: true) { _ in
    withAnimation(.easeInOut(duration: 0.5)) {
        gradientStops = GlowEffect.generateGradientStops()
    }
}
```

### 2. Color Customization
Modify the gradient colors to match your app's theme:

```swift
static func generateGradientStops() -> [Gradient.Stop] {
    [
        Gradient.Stop(color: Color(hex: "BC82F3"), location: Double.random(in: 0...1)),
        Gradient.Stop(color: Color(hex: "F5B9EA"), location: Double.random(in: 0...1)),
        Gradient.Stop(color: Color(hex: "8D9FFF"), location: Double.random(in: 0...1)),
        Gradient.Stop(color: Color(hex: "AA6EEE"), location: Double.random(in: 0...1)),
        Gradient.Stop(color: Color(hex: "FF6778"), location: Double.random(in: 0...1)),
        Gradient.Stop(color: Color(hex: "FFBA71"), location: Double.random(in: 0...1)),
        Gradient.Stop(color: Color(hex: "C686FF"), location: Double.random(in: 0...1))
    ].sorted { $0.location < $1.location }
}
```

### 3. Layer Customization
Fine-tune the effect's appearance by adjusting layer properties:

```swift
ZStack {
    // Base layer with no blur
    EffectNoBlur(gradientStops: gradientStops, width: 5)
        .onAppear {
            Timer.scheduledTimer(withTimeInterval: 0.25, repeats: true) { _ in
                withAnimation(.easeInOut(duration: 0.5)) {
                    gradientStops = GlowEffect.generateGradientStops()
                }
            }
        }
    
    // Blurred overlay layer
    Effect(gradientStops: gradientStops, width: 7, blur: 4)
        .onAppear {
            Timer.scheduledTimer(withTimeInterval: 0.3, repeats: true) { _ in
                withAnimation(.easeInOut(duration: 0.6)) {
                    gradientStops = GlowEffect.generateGradientStops()
                }
            }
        }
}
```

## Usage Examples

### Basic Implementation
```swift
struct ContentView: View {
    @State private var gradientStops: [Gradient.Stop] = []
    
    var body: some View {
        ZStack {
            // Your content here
            GlowEffect(gradientStops: gradientStops)
                .onAppear {
                    gradientStops = GlowEffect.generateGradientStops()
                }
        }
    }
}
```

### With Custom Parameters
```swift
struct CustomGlowView: View {
    @State private var gradientStops: [Gradient.Stop] = []
    
    var body: some View {
        ZStack {
            EffectNoBlur(gradientStops: gradientStops, width: 3)
            Effect(gradientStops: gradientStops, width: 5, blur: 3)
        }
        .onAppear {
            gradientStops = GlowEffect.generateGradientStops()
        }
    }
}
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the MIT License.

---

⭐️ If this project helped you, please consider giving it a star!
