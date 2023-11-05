# HW3
    
![IMG_0269](https://github.com/wuyodi/yzu-swiftUI-1121-1101511/assets/58367863/a97e72bd-e54e-4b0c-b068-fd2f2ff2ea24)

```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        ZStack {
            Image("A")
                .resizable() 
                .scaledToFit()
                .frame(width:700 , height: 500, alignment: .center)
            VStack{
                HStack(spacing:40){
                    VStack{
                        Text("福岡義勇")
                        Image("B1")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    VStack{
                        Text("戀柱")
                        Image("B2")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    VStack{
                        Text("東堂葵")
                        Image("D")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    
                }.padding([.trailing],10)
                HStack(spacing:40){
                    VStack{
                        Text("伏黑甚爾")
                        Image("Fu")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    VStack{
                        Text("魯夫")
                        Image("Lufo")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    VStack{
                        Text("紅髮傑克")
                        Image("R")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    
                }.padding([.trailing],10)
                HStack(spacing:40){
                    VStack{
                        Text("熊貓")
                        Image("Panda")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    VStack{
                        Text("亞古獸")
                        Image("Y")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                    }
                    VStack{
                        Text("術儺")
                        Image("Su")
                            .resizable()
                            .scaledToFit()
                            .frame(width:60 , height: 120, alignment: .center)
                        
                    }
                }.padding([.trailing],10)
            }    
        }
    }
}


```
