# 시작하기 - Tabbed App 템플릿

출력내용

/Users/hngfu/Documents/swift-photoframe/PhotoFrame/PhotoFrame/FirstViewController.swift 18 viewDidLoad() 40
/Users/hngfu/Documents/swift-photoframe/PhotoFrame/PhotoFrame/SecondViewController.swift 17 viewDidLoad() 40

## 스텝2

#file - 해당 메서드가 있는 파일의 경로 및 파일명

#line - 호출 되는 곳이 위에서 몇번째 줄에 있는지
#function - 해당 메서드의 이름
#column - 호출되는 곳이 왼쪽에서 몇번째에 있는지 

#### UILabel 클래스 속성(Property)는 어떤게 있는지

var text: String? - Label 글자를 나타낸다.
var textColor: UIColor! - Label 글자의 색상을 나타낸다.
var backgroundColor: UIColor? - Label의 배경색을 나타낸다.
var alpha: CGFloat - Label의 투명도를 나타낸다.
var font: UIFont! // default is nil (system font 17 plain) - Label의 폰트 관련된 속성을 담당.

- 스텝2 사진
![step2](https://user-images.githubusercontent.com/38850628/49932117-98517b00-ff0b-11e8-8186-c2641baeb5e8.png)

## 스텝3

- 버튼에 IBAction을 추가할 때 이벤트(Event) 종류에는 어떤 것들이 있는지
메서드 이름 설정, 어떠한 상황에서 메서드를 실행할지(예를들어 손가락을 뗏을때 실행한다.)

- 버튼에 액션을 여러개 추가할 수 있을까? 추가할 수 있다.
![](https://user-images.githubusercontent.com/38850628/49980196-d0050500-ff95-11e8-9c8e-4ebbb9319c9a.png)

- 버튼이 여러일 때 하나의 액션에 추가할 수 있을까? 추가할 수 있다.
![](https://user-images.githubusercontent.com/38850628/49980315-528dc480-ff96-11e8-9a2d-ccc504a7a4e4.png)

- 스텝3 변경 전 사진
![stepBefore](https://user-images.githubusercontent.com/38850628/49979836-2ffaac00-ff94-11e8-8284-ecbd9bf5c499.png)

- 스텝3 변경 후 사진
![step3After](https://user-images.githubusercontent.com/38850628/49979837-2ffaac00-ff94-11e8-8627-668274c58adb.png)

## 스텝4
- Seque에 액션에 있는 여러 항목들은 어떤 효과가 있는지

일단 가장먼저 scene이 아래에서 위로 올라오는 애니메이션 효과가 default로 되어있는데 애니메이션 효과를 끌 수 있다.
그리고 식별자를 지정하거나 클래스를 연결해줄 수 있다.

모달형식, 팝업형식으로 띄우도록 설정 가능하다.

- 버튼을 이용해 segue를 연결하는 방법 말고도 manual segue라고 컨트롤러를 이용하여 연결하는 방법도 있다.

- 스텝4 새로운 화면
![](https://user-images.githubusercontent.com/38850628/49981137-d09f9a80-ff99-11e8-8b2a-c0f09478e2f6.png)

## 스텝5

- 화면 전환이 이루어지는 사이에 뷰컨트롤러 라이프사이클이 어떻게 변화하는지 학습한다.

GreenViewController.swift 20 viewWillAppear 40
GreenViewController.swift 24 viewDidAppear 40
GreenViewController.swift 28 viewWillDisappear 40
YellowViewController.swift 20 viewWillAppear 40
YellowViewController.swift 24 viewDidAppear 40
GreenViewController.swift 32 viewDidDisappear 40

초록화면 WillDisappear가 나오고 노랑화면이 Appear되고 초록화면 DidDisappear이 나온다.
*DidDisappear은 다음 뷰가 Will,DidAppear된 후 콜백된다.*

- YellowViewController에서 Segue를 제거하고 다음 화면을 보여줄 때 코드로 보여주는 방법을 찾아보고 적용해본다.

manual segue를 만들고 segue의 identifier에 값을 주고
```swift
self.performSegueWithIdentifier("identifier값", sender: self)
```
명령어를 통해 다음 화면을 보여줄수있다.

![](https://user-images.githubusercontent.com/38850628/49986665-149f9900-ffb4-11e8-8452-a7e52611c37c.png )


## 스텝6

- 뷰 컨트롤러 콜백 함수들 동작도 동일한지 확인한다. 다르게 동작한다.

GreenViewController.swift 20 viewWillAppear 40
GreenViewController.swift 24 viewDidAppear 40
GreenViewController.swift 28 viewWillDisappear 40
YellowViewController.swift 20 viewWillAppear 40
GreenViewController.swift 32 viewDidDisappear 40
YellowViewController.swift 24 viewDidAppear 40

*GreenViewController가 DidDisappear되고 YellowViewController가 DidAppear된다.*

- 뷰컨트롤러 컨테이너 동작을 이해한다.

화면에 콘텐츠를 표기하지 않고 뷰컨트롤러들을 가지고 있다.
하나의 뷰 컨트롤러에서 다른 뷰 컨트롤러로 자연스럽게 이어지도록 다양한 수단을 제공.

- 뷰컨트롤러 컨테이너는 또 어떤 클래스가 있는지 찾아보고 학습한다.

Navigation Controllers
Tab Bar Controllers
Page View Controllers
Split View Controllers
Popovers

![](https://developer.apple.com/library/archive/documentation/WindowsViews/Conceptual/ViewControllerCatalog/Art/intro.png)
출처 - developer.apple.com

- 내비게이션 컨트롤러가 있을 경우와 없을 경우 화면 전환 동작이 어떻게 다른지, 화면들 포함관계가 있는지 학습한다. 내비게이션 컨트롤러 관련 메서드가 왜 push / pop 인지 학습한다.

일반적으로는 'present' 메서드로 view를 띄우고 'dismiss'메서드로 view를 닫는다.
하지만 내비게이션 컨트롤러는 스택구조로 되어있다. 그렇기 때문에 뷰를 닫을때 'popViewController' 메서드를 이용하여 닫는다.

![](https://user-images.githubusercontent.com/38850628/50056000-6f461a00-0199-11e9-85a2-96e76437b620.png)
출처 - developer.apple.com

스텝6 화면
![](https://user-images.githubusercontent.com/38850628/50056086-b84a9e00-019a-11e9-924f-15ad0650a07d.png)

## 스텝7

- UIImageView 와 UIImage 클래스는 각각 어떤 역할을 담당하는지 학습한다.

UIImage: 이미지 데이터를 관리하는 객체

UIImageView: 단일 이미지 또는 연속적인 애니메이션 이미지를 표시하는 객체

- 이미지 뷰의 속성은 어떤 것들이 있는지 애플 개발자 문서를 참고한다.

contentMode 속성은 이미지를 어떻게 보여줄지를 결정한다.

투명도 조절이나, 강조, 동적인 이미지를 start, stop할 수 있는 속성들이 있다.

스텝7 화면
![](https://user-images.githubusercontent.com/38850628/50056590-76712600-01a1-11e9-9495-6614e638333f.png)

## 스텝8

![](https://user-images.githubusercontent.com/38850628/50057162-ef747b80-01a9-11e9-954c-6389e5db3f0f.png)
![](https://user-images.githubusercontent.com/38850628/50057163-ef747b80-01a9-11e9-94f6-49387f3f3e02.png)
![](https://user-images.githubusercontent.com/38850628/50057164-ef747b80-01a9-11e9-8228-36ff178c97ce.png)
![](https://user-images.githubusercontent.com/38850628/50057165-f00d1200-01a9-11e9-868e-7f611de50082.png)
