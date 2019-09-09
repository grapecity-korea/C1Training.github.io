---
title: ComponentOne for ASP.NET | 내비게이션
keywords: ComponentOne, ASP.NET, 웹폼, 내비게이션, navigation
tage: [ 메뉴, menu, file explorer ]
last_updated: Aug 08, 2019
summary: "ComponentOne for ASP.NET 이 제공하는 내비게이션 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1asp_nav.html
folder: mydoc
---


## C1Menu 다양한 레벨의 메뉴 만들기

[C1 메뉴 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1Menu.zip)

본문은 C1Menu를 사용하여 다양한 레벨의 메뉴 만들기를 소개합니다. C1Menu를 한 데이터 소스 및 애니메이션 효과 등에 바인딩합니다.

C1Menu는 애니메이션 효과, 이미지, 체크상자 내의 항목 및 조정 항목 스크롤 표시 등을 사용하여 다양한 레벨의 메뉴를 만들 수 있습니다. 심지어 당신의 응용프로그램에서 컨텍스트가 지원하는 팝업메뉴를 만들 수 있습니다.

두 가지 각기 다른 스타일의 메뉴의 구체적인 방법은 다음과 같습니다. ：

  

### 기본메뉴

C1Menu를 페이지에 추가합니다.

C1Menu의 DataBindings을 통해 C1의 MenuItem을 설정합니다. 메뉴와 서브메뉴를 수평과 수직으로 표시합니다. 코드는 다음과 같습니다. ：

  

```html
<DataBindings>
<wijmo:C1MenuItemBinding DataMember="Menuitem" HeaderField="header" 
NavigateUrlField="navigateUrl" SeparatorField="separator" TextField="text" />
</DataBindings>
```

C1Menu의 HideAnimation를 통해 애니메이션 감추기를 설정합니다. 코드는 다음과 같습니다. ：

```html
<HideAnimation>
<Animated Effect="fade"></Animated>
</HideAnimation>
```

### IPod 스타일 메뉴

C1Menu를 페이지에 추가합니다.

데이터소스를 App_Data폴더에 추가합니다.

C1Menu의 HideAnimation를 통해 애니메이션 감추기를 설정합니다. 코드는 다음과 같습니다. ：

```html
<asp:XmlDataSource ID="XmlDataSource1" runat="server" 
DataFile="~/App_Data/menu_structure.xml" XPath="/root/menuitem">
</asp:XmlDataSource>
```

C1Menu의 DataBindings을 통해 XML데이터소스를 바인딩합니다. 또한 Mode를 통해 IPod스타일의 수직메뉴를 설정합니다. 코드는 다음과 같습니다. ：

```html
<wijmo:C1Menu runat="server" ID="Menu2" Mode="Sliding" DataSourceID="XmlDataSource1">
</wijmo:C1Menu>
```

C1Menu는 톱 레벨 메뉴, 서브메뉴 및 서브그룹을 스크롤 표시할 수 있습니다.  
스크롤모드 옵션을 버튼클릭 스크롤, 버튼 하버 스크롤, 테두리 순회스크롤 또는 스크롤 바로 설정할 수 있습니다.

두 가지 메뉴의 구체적인 실행 결과는 다음 그림과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc2-1-1.gif)

본문 Demo의 소스코드는 다음과 같습니다. :

[C1 메뉴 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1Menu.zip)


## FileExplorer 컨트롤 입문

[FileExplorer 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TextC1FileExplorer.zip)

처음  ConponentOne  컨트롤을 사용하면 그 강화된 기능에 놀라게 됩니다. 수많은 코드를 통해 비로소 완성되는 것들을 이 컨트롤을 사용하면 드래그만으로 만들어낼 수 있습니다. 실로 코딩 엔지니어에게는 꿈 같은 일이지요. 아래는  C1FileExplorer의 소개 및 입문과 관련된 내용입니다.

  

C1FileExplorer는 Windows 익스플로러의 기능을 완전히 모방하여 C1컨트롤에서 만든 것입니다. 우리는 이것을 쉽게 자신의 웹 페이지에 추가하여 새 폴더 만들기, 이름 바꾸기, 폴더 삭제나 복사 등이 가능한 파일과 폴더를 구성할 수 있습니다.  
더욱 주목해야 할 것은 키보드로 이런 것들이 가능하다는 것입니다.  C1FileExplorer는 사용자 정의 바로가기 인터페이스를 제공합니다.

C1FileExplorer는 여러 가지 레이아웃의 작성을 지원하여 상세정보표시 또는 간단한 표시 같은 폴더/파일의 표시방법을 설정할 수 있습니다. 또한 그것으로 일부 컨트롤(툴 바, addressbox 등)의 기능을 감출 수 있습니다.  
너무 많은 파일 리스트가 있는 경우,  Filtering설정을 통해 특정한 폴더/파일만 보이게 하거나 페이지 나누기를 할 수 있습니다.

  

여기까지  C1FileExplorer의 일부 기능을 언급했습니다. 강화된 기능의 이 컨트롤을 배워봅시다. 아래의 코드는 모두 C#으로 작성되었습니다.

  

**Step1**

먼저, ASP.Net Web응용프로그램을 만든 후, Web폼을 추가해야 합니다. 그리고 툴 바에서 C1FileExplorer 컨트롤을 찾아Web 폼에 드래그합니다. 툴 바에 C1FileExplorer 가 없는 경우, 오른쪽을 클릭하여 “옵션항목”에서 C1FileExplorer를 선택하여 추가하면 됩니다.  
코드는 다음과 같습니다. ：

```html
<div>
<cc1:C1FileExplorer ID="C1FileExplorer1" InitPath="./picture" runat="server">
</cc1:C1FileExplorer>
</div>
```

실행결과는 다음과 같습니다.：

![](https://www.grapecity.co.kr/images/training/c1/tc2-2-1.png)

  

**Step2**

아래에서 우리는 InitPath를 자신의 디렉터리로 변경해야 합니다. 해당 디렉터리를 자신이 작성한 모든 프로젝트에 두지 않도록 주의합니다.  
필자는 프로젝트 디렉터리에 picture 폴더를 만들었고 몇 개의 사진을 저장했습니다. IninPath를 일부 변경한 코드는：

```csharp
InitPath="./picture"。
```

모두 변경한 실행결과는 다음과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc2-2-2.png)

  

아래에서 우리는 FileExplorer의 특성을 시험해볼 수 있습니다. ：

  

**1. 페이지 나누기**

파일이 너무 많은 경우라도 페이지 나누기 관리를 할 수 있습니다. AllowPaging 속성을 true로 설정하기만 하면 됩니다.  
코드는 다음과 같습니다. ：

```html
<div>
<cc1:C1FileExplorer ID="C1FileExplorer1" InitPath="./picture" runat="server" AllowPaging = true PageSize=5>
</cc1:C1FileExplorer>
</div>
```

실행결과는 다음과 같습니다. :

![](https://www.grapecity.co.kr/images/training/c1/tc2-2-3.png)

  

**2. 다수 파일의 선택**

AllowMultipleSelection속성을 true로 설정하면 됩니다.

```html
<div>
<cc1:C1FileExplorer ID="C1FileExplorer1" InitPath="./picture" runat="server" AllowMultipleSelection="true">
</cc1:C1FileExplorer>
</div>
```

실행결과는 다음과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc2-2-4.png)

  

**3. 관리파일 만들기**

Web의 페이지에서 오른쪽을 클릭하면 아래의 그림처럼 태그를 볼 수 있습니다. 사용자가 파일을 편리하게 관리할 수 있습니다.

![](https://www.grapecity.co.kr/images/training/c1/tc2-2-5.png)

  

**4. 파일실행 제한**

사용자가 위의 그림에서 나타낸 모든 기능을 원하지 않는 경우, 그것을 차단해버릴 수 있습니다. 대응하는 속성을 False로 설정하기만 하면 됩니다.  
다음과 같이 설정하여 열기, 새로 만들기, 복사 등의 기능을 차단할 수 있습니다 ：  
EnableCopy=false  
EnableOpenFile=false  
EnableCreateNewFolder=false  
코드는 다음과 같습니다. ：

```html
<div>
<cc1:C1FileExplorer ID="C1FileExplorer1" InitPath="./picture" runat="server" AllowMultipleSelection="true" EnableCopy=false EnableOpenFile=false EnableCreateNewFolder=false>
</cc1:C1FileExplorer>
</div>
```

그 표시결과는 다음과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc2-2-6.png)

  

FileExplorer의 더 많은 기타 특성에 흥미가 있다면 스스로 테스트해보세요.

[FileExplorer 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TextC1FileExplorer.zip)