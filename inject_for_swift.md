## Inject
- packge repo - [Inject](https://github.com/krzysztofzablocki/Inject)
- it's a package which allows hot-reloading when developing in Swift + XCode + Simulator 
  - it's better than using XCode's preview canvas

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
 
```swift
struct ContentView: View {
    @ObserveInjection var inject

    var body: some View {
    ...
    .enableInjection()
  }
}
```


### Screenshots
- 
