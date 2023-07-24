# Use-SwiftUI-in-Playground

```swift
import SwiftUI
import PlaygroundSupport

class FooController: ObservableObject {
    @Published var flag1 = false
    @Published var flag2 = true
}

let controller = FooController()

struct ContentView: View {
    
    @EnvironmentObject var controller: FooController
    
    var body: some View {
        NavigationView {
            VStack {
                Text("flag2: \(controller.flag2.description)")
                NavigationLink("", destination: Text("Destination").onTapGesture {
                    controller.flag1.toggle()
                }, isActive: $controller.flag1)
                Button("Tap me") { controller.flag1.toggle() }
            }
            
        }
    }
}

PlaygroundPage.current.setLiveView(ContentView().frame(width: 200, height: 200).environmentObject(controller))
```
