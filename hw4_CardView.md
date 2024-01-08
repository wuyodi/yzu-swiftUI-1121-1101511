# HW4_CardView

```swift
import SwiftUI

struct TermAndDescription: Identifiable{
    var id = UUID()
    var term:String
    var description:String
}
var myDictionary = [
    TermAndDescription(term: "星期一", description: "猴子穿新衣"),
    TermAndDescription(term: "星期二", description: "猴子肚子餓"),
    TermAndDescription(term: "星期三", description: "猴子去爬山"),
    TermAndDescription(term: "星期四", description: "猴子看電視")
    
]

struct CardView: View{
    @State var currentCard = 0
    var body: some View{
        VStack{
            VStack{
                Text(myDictionary[currentCard].term)
                    .font(.title)
                    .padding(.all, 10)
                Text(myDictionary[currentCard].description)
                    .font(.body)
                    .foregroundColor(.blue)
                .padding(.all, 10)}
            .frame(minWidth: 0, idealWidth: 100, maxWidth: 300, minHeight: 0, idealHeight: 100, maxHeight: 300, alignment: .center)
            .background(Color.yellow)
            .onTapGesture{
                if currentCard<myDictionary.count-1{
                    currentCard+=1
                }else{
                    currentCard=0
                }
            }
            Text("點擊查看下一張")
                .padding(.all, 10)
        }
    }
}





```
