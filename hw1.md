# HW1
    
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
                        .cornerRadius(/*@START_MENU_TOKEN@*/3.0/*@END_MENU_TOKEN@*/, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
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
            } .padding(/*@START_MENU_TOKEN@*/10/*@END_MENU_TOKEN@*/)
        }
    }
}



```
