# HW1
   ![IMG_0267](https://github.com/wuyodi/yzu-swiftUI-1121-1101511/assets/58367863/784b6d46-21c2-4eae-881c-20f556d96f5e)
 
```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        ZStack{
            Image("Yodi")
                .resizable()
                .aspectRatio(contentMode: .fill)
            
            VStack{
                HStack{
                    Text("1101511 吳宥德")
                        .fontWeight(.heavy)
                        .font(.system(size:20))
                    Image(systemName: "square.and.arrow.up")
                        .background(Color.cyan)
                        .cornerRadius(3.0)
                }
                Spacer()
                Text("You can’t be perfect but you can be unique.")
                    .fontWeight(.heavy)
                    .lineSpacing(20)
                    .font(.system(size: 30.0))
                    .foregroundColor(.white)
                    .frame(width: 350, height: 150, alignment: .center)
                    .background(Color.blue)
                    .cornerRadius(30.0)
                    .opacity(0.8)
            } .padding(10)
        }
    }
}



```
