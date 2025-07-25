## Inject
- packge repo - [Inject](https://github.com/krzysztofzablocki/Inject)
- it's a package which allows hot-reloading when developing in Swift + XCode + Simulator 
  - it's better than using XCode's preview canvas

- NOTE - WIP, not confirmed to work -

### Checklist for daily use
- InjectionIII is in "File Watcher" mode with the correct project selected
- Inject is a package dependency of the Swift project
- The target within the project > General > Frameworks, Libraries, and Embedded Content > contains `Inject`
- Swift project Build Settings Other Linker Flags Debug is "-Xlinker -interposable"
- Build Settings > User-Defined contains `EMIT_FRONTEND_COMMAND_LINES` value of `YES`
- An `InjectionSetup.swift` file exports the `Inject` import:
```swift
#if DEBUG
/// Makes Inject available in each file without using `import Inject` at the top of each file
@_exported import Inject
#endif
```
- The view to hot reload uses `@ObserveInjection var inject` and `.enableInjection()`
```swift
import SwiftUI

struct ContentView: View {
    @ObserveInjection var inject
    
    var body: some View {
        VStack {
            Image(systemName: "globe")
                .imageScale(.large)
                .foregroundStyle(.tint)
            Text("Hello, world")
        }
        .padding()
        .enableInjection()
    }
}

#Preview {
    ContentView()
}
```


### Set up
- The instructions in the repo readme are not clear so I'm writing up steps I can reference in the future
- Prereqs:
  - XCode, Swift project, Simulator and the knowledge of how to use these together 
- One time per machine:
  - Download InjectionIII's latest zip from [here](https://github.com/johnno1962/InjectionIII/releases), unzip it, move it to the `Applications` folder, open it (it appears in the menu bar), select the project folder (the folder containing a `.xcodeproj`)
    - for convenience, MacOS Settings > Login Items > add it
  - Select the project in XCode > Build Settings > Search "Other Linker" > Set "Debug" string to `-Xlinker -interposable`
- Per project:
  - Add `Inject` as a dependency - open the project in XCode > "File" > "Add Package Dependencies..." > in the search bar in the top right of the menu paste `https://github.com/krzysztofzablocki/Inject`
  - In Build Settings click "+" and "Add User Defined Setting" with name of `EMIT_FRONTEND_COMMAND_LINES` and value of `YES`
- Then follow the workflow integration part [here](https://github.com/krzysztofzablocki/Inject?tab=readme-ov-file#workflow-integration)
- 

### Other
- Helpful video - https://www.youtube.com/watch?v=kk1DnjyLpUE


### Screenshots
- 
