# 🌅 SwiftUIImageViewer

A fullscreen image viewer with pinch-zooming built using SwiftUI.

![image](https://media.giphy.com/media/68H9UkT4pYKXpnCkkj/giphy.gif)

# 👩‍🔧 Installation

File -> Swift Packages -> Add Package Dependancy..

```Swift
https://github.com/fuzzzlove/swiftui-image-viewer.git
```

# 👩‍💻 Usage

```Swift
import SwiftUI
import SwiftUIImageViewer

struct ContentView: View {

    @State private var isImagePresented = false

    var body: some View {
        image
            .resizable()
            .scaledToFit()
            .cornerRadius(12)
            .frame(width: 260, height: 260)
            .onTapGesture {
                isImagePresented = true
            }
            .fullScreenCover(isPresented: $isImagePresented) {
                SwiftUIImageViewer(image: image)
                    .overlay(alignment: .topTrailing) {
                        closeButton
                    }
            }
    }

    private var image: Image {
        Image("dogs")
    }

    private var closeButton: some View {
        Button {
            isImagePresented = false
        } label: {
            Image(systemName: "xmark")
                .font(.headline)
        }
        .buttonStyle(.bordered)
        .clipShape(Circle())
        .tint(.purple)
        .padding()
    }
}
```

