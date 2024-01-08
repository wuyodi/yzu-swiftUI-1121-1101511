#HW4_ContentView

```swift

import SwiftUI

struct ContentView: View{
    var body:some View{
        VStack{
            //  TabView{
            Group{
                Text("Yodi 的世界")
                    .font(.largeTitle)
                    .fontWeight(.heavy)
                    .foregroundStyle(.primary)
                TabView{
                    WelcomeView()
                        .tabItem{
                            Image(systemName: "rosette")
                            Text("Welcome")
                        }

https://github.com/wuyodi/yzu-swiftUI-1121-1101511/assets/58367863/35d780a7-5309-42f5-bb27-9297da17075e


                    CourseListlView()
                        .tabItem{
                            Image(systemName: "list.dash")
                            Text("Courses")
                        }
                    CardView()
                        .tabItem{
                            Image(systemName: "book")
                            Text("Learn")
                        }
                }
            }
            .toolbarBackground(Color.black, for: .tabBar)
            .toolbarBackground(.visible, for:.tabBar)
            //.toolbarColorScheme(.dark, for: .tabBar)}
        }.tint(.yellow)
        //}
    }
}

struct WelcomeView:  View{
    var body: some View{
        VStack{
            Image("Me")
                .resizable()
                .aspectRatio(contentMode: .fit)
            Text("A…A…A…(我是波吉\n大家好")
                .fontWeight(.heavy)
                .lineSpacing(20)
                .font(.system(size: 32.0))
                .foregroundColor(.white)
                .frame(width: 350, height: 150, alignment: .center)
                .background(Color.teal)
                .cornerRadius(20.0)
                .multilineTextAlignment(.center)
        }
    }
}

```
