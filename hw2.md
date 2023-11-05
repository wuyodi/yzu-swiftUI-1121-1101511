# HW2



https://github.com/wuyodi/yzu-swiftUI-1121-1101511/assets/58367863/9aedc7db-fdbe-46c8-a996-a58919f55196



![IMG_0270](https://github.com/wuyodi/yzu-swiftUI-1121-1101511/assets/58367863/8f76608a-ac9f-473d-a6e5-1c1871710737)


```swift

import SwiftUI

struct ContentView: View {
    @State var gametimes: Int = 1
    @State var rulename: String = "一把定勝負"
    @State var computerPushImage: String = "Game"
    @State var computerWinCount: Int = 0
    @State var userWinCount: Int = 0
    @State var winName: String = ""
    @State var winMessage: String = ""
    @State var gameTotal: Int = 1
    @State var isShowWinner: Bool = false
    @State var gameModels = ["Rock", "Paper", "Scissors"]
    @State var selectedImage: String = ""
    @State var isSelected: Bool = false
    var body: some View {
        VStack {
            TitleView()
            ruleView()
            computerPush()
            Spacer()
            Spacer()
            Spacer()
            Spacer()
            if isSelected{
                personPush()
            }else{
                personSelected()
            }
            Spacer()
            playGame()
        }.padding()
            .alert(isPresented: $isShowWinner) {
                showResult()
            }
    }
}

struct TitleView: View {
    var body: some View {
        VStack {
            Text("剪刀石頭布") 
                .font(.title)
                .fontWeight(.bold)
        }
    }
}

extension ContentView{
    func computerPush() -> some View {
        Image(computerPushImage)
            .resizable()
            .aspectRatio(contentMode: .fit)
            .frame(width: 350)
            .clipShape(Circle())
    }
}

// 用戶選牌
extension ContentView{
    func personSelected() -> some View {
            HStack {
                    ForEach(gameModels.indices, id: \.self) { item in
                            Image(gameModels[item])
                                .resizable()
                                .aspectRatio(contentMode: .fit)
                                .frame(width: 80)
                                .clipShape(Circle())
                                .onTapGesture {
                                        selectedImage = gameModels[item]
                                        self.isSelected = true
                                    }
                        }.frame(minWidth: 0, maxWidth: .infinity)
                }
    }
}


// 用戶出牌
extension ContentView{
    func personPush() -> some View {
            Image(selectedImage)
                .resizable()
                .aspectRatio(contentMode: .fit)
                .frame(width: 120)
                .clipShape(Circle())
                .onTapGesture {
                        self.isSelected = false
                    }
    }
}



extension ContentView{
    func randomPush() {
        let index = Int.random(in: 0 ... 2)
        computerPushImage = gameModels[index]
        gametimes -= 1
    }
}



// 立即猜拳
extension ContentView{
    func playGame() -> some View {
            Text("立即猜拳")
                .font(.system(size: 17))
                .frame(minWidth: 0, maxWidth: .infinity, minHeight: 10, maxHeight: 32)
                .padding()
                .foregroundColor(.white)
                .background(Color(red: 51 / 255, green: 51 / 255, blue: 51 / 255))
                .cornerRadius(8)
                .onTapGesture {
            if isSelected {
                    randomPush()
                    showWinner()
                            }
                    }
    }
}



extension ContentView{
    func ruleView() -> some View {
            Menu {
                    Button("一把定勝負") {
                        self.gametimes = 1
                        self.rulename = "一把定勝負"
                        self.gameTotal = 1
                        }
                    Button("三戰兩勝") {
                            self.gametimes = 3
                            self.rulename = "三戰兩勝"
                            self.gameTotal = 3
                        }
                    Button("五戰三勝") {
                            self.gametimes = 5
                            self.rulename = "五戰三勝"
                            self.gameTotal = 5
                        }
                } label: {
                        Label(rulename, systemImage: "slider.horizontal.3")
                            .foregroundColor(.gray)
                            .frame(minWidth: 0, maxWidth: .infinity, minHeight: 10, maxHeight: 60)
                            .background(Color(.systemGray6))
                            .cornerRadius(8)
                    }
    }
}


// 判斷遊戲是否結束
extension ContentView{
    func isEndGame() {
        if gameTotal == 5 && computerWinCount == 3 || gameTotal == 3 && computerWinCount == 2 || gameTotal == 1 && computerWinCount == 1 {
            computerWinCount = 0
            userWinCount = 0
            gametimes = gameTotal //reset
            winName = "你輸了"
            winMessage = "遊戲結束"
        } else if gameTotal == 5 && userWinCount == 3 || gameTotal == 3 && userWinCount == 2 || gameTotal == 1 && userWinCount == 1 {
            computerWinCount = 0 //reset
            userWinCount = 0 //reset
            gametimes = gameTotal //reset
            winName = "你贏了"
            winMessage = "遊戲結束"
        }
        isShowWinner = true
    }      
} 
    



// 判斷最終猜拳结果
extension ContentView{
    func showWinner() {
            if computerPushImage == "Rock" && selectedImage == "Paper" || computerPushImage == "Paper" && selectedImage == "Scissors" || computerPushImage == "Scissors" && selectedImage == "Rock" {
                    winName = "你贏了"
                    userWinCount += 1
                    winMessage = "你還有" + String(gametimes) + "次機會"
                    isEndGame()
                } else if computerPushImage == selectedImage {
                    gametimes += 1
                    winName = "平手"
                    winMessage = "你還有" + String(gametimes) + "次機會"
                    isEndGame()
                    } else {
                    winName = "你輸了"
                    computerWinCount += 1
                    winMessage = "你還有" + String(gametimes) + "次機會"
                    isEndGame()
                        }
    }
}



// 展示猜拳结果
extension ContentView{
    func showResult() -> Alert {
            let alert = Alert(
                    title: Text(winName),
                    message: Text(winMessage),
                    dismissButton: .default(Text("繼續")) {
                            self.computerPushImage = "Game"
                            self.isSelected = false
                        }
                )
            return alert
    }
}



```
