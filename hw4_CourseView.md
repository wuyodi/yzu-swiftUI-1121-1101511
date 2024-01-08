# HW4_CourseView

```swift

import SwiftUI

struct Course:Identifiable{
    var id=UUID()
    var name:String
    var image:String
    var description:String
}
var courses = [
    Course(name: "魯夫", image: "Lofu", description: "我要成為海賊王！"),
    Course(name: "索隆", image: "索隆", description: "我要成為世界第一劍豪！"),
    Course(name: "喬巴", image: "喬巴", description: "我要成為一個醫生"),
    Course(name: "香吉士", image: "香吉士", description: "我喜歡女人"),
    Course(name: "羅傑", image: "羅傑", description: "想要我的財寶嗎 我全都放在那裡了")]

struct BasicImageRow: View{
    var thisCourse:Course
    var body: some View{
        HStack{
            Image(thisCourse.image)
                .resizable()
                .frame(width: 40, height: 40)
                .cornerRadius(5)
            Text(thisCourse.name)
        }
    }
}

struct CourseDetailView:View{
    @Environment(\.presentationMode) var presentationMode 
    var thisCourse: Course
    var body: some View{
        ScrollView{
            VStack{
                Image(thisCourse.image)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisCourse.name)
                    .font(.system(.title, design:.rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisCourse.description)
                    .font(.system(.subheadline, design:.rounded))
                    .fontWeight(.light)
                Spacer()
            }
        }
        .overlay(
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label:{
                        Image(systemName:"chevron.down.circle.fill")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                    })
                    .padding(.trailing, 20)
                    .padding(.top, 40)
                    Spacer()
                }
            }
        )
    }
}

struct CourseListlView:View{
    
    @State var showDetailView = false
    @State var selectedCourse:Course?
    
    var body: some View{
        NavigationView{
            List(courses){ courseItem in 
                BasicImageRow(thisCourse: courseItem)
                    .onTapGesture{
                        self.showDetailView = true
                        self.selectedCourse = courseItem
                    }
            }
            .sheet(item: self.$selectedCourse){ thisCourse in 
                CourseDetailView(thisCourse: thisCourse)
            }
            .navigationBarTitle("海賊王角色")
        }
    }
}


```
