---
title: ComponentOne Enterprise 2019 V3 새로운 기능
sidebar: home_sidebar
keywords: news, blog, updates, release notes, announcements
permalink: 2019v3_whatsnew.html
folder: news
summary: "ComponentOne 2019 v3을 발표하게 되어 매우 기쁘게 생각합니다. 이 버전은 새로운 컨트롤, .NET Core 3 뉴스, 리본 업데이트 등이 포함된 흥미로운 릴리스로서, WinForms, ASP.NET 및 WPF를 위해 제공되는 당사의 가장 인기 있는 컨트롤의 향상된 기능도 포함되어 있습니다.
당사에서는 첫 번째 기본 Blazor 컨트롤을 소개하고 있습니다. Blazor를 사용하면 개발자는 서버와 클라이언트에서 기존 C# 프로그래밍 기술을 사용하여 풍부한 웹 응용 프로그램을 구축할 수 있습니다. ComponentOne Blazor Edition은 HTML, JavaScript 및 CSS 환경을 많이 사용하지 않고도 C#을 사용하여 개발할 수 있는 필수 UI 컨트롤을 제공하도록 디자인되었습니다."
---
# 새 릴리스! ComponentOne 2019 V3

[ComponentOne](https://www.grapecity.co.kr/componentone-enterprise) 2019 v3을 발표하게 되어 매우 기쁘게 생각합니다. 이 버전은 새로운 컨트롤, .NET Core 3 뉴스, 리본 업데이트 등이 포함된 흥미로운 릴리스로서, WinForms, ASP.NET 및 WPF를 위해 제공되는 당사의 가장 인기 있는 컨트롤의 향상된 기능도 포함되어 있습니다.

당사에서는 첫 번째 기본 Blazor 컨트롤을 소개하고 있습니다. Blazor를 사용하면 개발자는 서버와 클라이언트에서 기존 C# 프로그래밍 기술을 사용하여 풍부한 웹 응용 프로그램을 구축할 수 있습니다. ComponentOne Blazor Edition은 HTML, JavaScript 및 CSS 환경을 많이 사용하지 않고도 C#을 사용하여 개발할 수 있는 필수 UI 컨트롤을 제공하도록 디자인되었습니다.

## Blazor 및 웹 업데이트

### Blazor(베타)를 위한 첫 번째 데이터 그리드 및 입력 컨트롤 발표

2019 v3에서 새롭게 선보이는 ComponentOne Blazor Edition(Beta)은 처음부터 Blazor용으로 구축된 기본 UI 컨트롤 세트입니다. 당사의 최고 크로스 플랫폼 데이터 그리드인 FlexGrid와 AutoComplete, CheckBox 및 ComboBox를 포함한 몇 가지 입력 컨트롤을 사용하여 서버 및 클라이언트 측 C# 웹 응용 프로그램을 완성해 보십시오.

이 컨트롤을 사용하려면 C1ControlPanel 설치 프로그램(다운로드 링크)에서 다운로드하면 됩니다.

[Blazor Explorer 데모](https://demos.componentone.com/blazor/blazorexplorer/)

### ASP.NET용 FlexGrid에서 다중 범위 선택 가능

사용 가능한 가장 유연한 셀 선택 모델이 없으면 FlexGrid라고 할 수 없습니다. 이 릴리스에서는 사용자가 CTRL(또는 command) 키를 누른 채 여러 셀 범위를 선택할 때 사용할 수 있는 다중 범위 선택 기능을 추가했습니다. FlexGrid에서 이 동작을 지원하기 위해 MultiRange라는 새로운 선택 모드와 선택한 CellRange 개체를 포함하는 배열을 반환하는 새로운 **selectedRanges** 속성을 추가했습니다.

![새 릴리스! ComponentOne 2019 v3!](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/1-FlexGrid-MultiRange%20Selection.png)

또한 ASP.NET Core MVC용 FlexGrid에는 사용자가 드문 경우에 성능을 조정하려고 할 때 사용할 수 있는 몇 가지 새로운 API가 있습니다. 대부분의 사람들은 이 API를 사용할 필요가 없지만 사용하려는 사람들을 위해 추가했습니다. 이 API를 사용할 때는 반드시 설명서를 주의 깊게 읽으십시오.

- **refreshRange** 메서드
- **LazyRender** 속성
- **RefreshOnEdit** 속성

### ASP.NET용 FlexSheet에서 자동 채우기 가능

Excel 사용자는 이제 ASP.NET Core MVC용 FlexGrid에서도 지원되는 자동 채우기 기능을 이용할 수 있습니다. 자동 채우기 기능을 사용하면 Excel에서와 마찬가지로 패턴을 기반으로 선택한 셀을 채울 수 있습니다. 이 기능은 **AllowAutoFill** 속성을 설정하면 사용할 수 있습니다.

![새 릴리스! ComponentOne 2019 v3!](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/2%20-FlexSheet-AutoFill.png)

### 새로운 계단 꺾은선형 차트 유형을 FlexChart에 추가

ASP.NET Core MVC용 FlexChart는 이제 Step, StepSymbol 및 StepArea 차트를 지원합니다. 이 차트는 이자율 vs 시간과 같이 불규칙적인 시간 간격으로 변화하는 모든 유형의 데이터를 표시하는 데 유용합니다.

![새 릴리스! ComponentOne 2019 v3!](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/3%20-StepChart.png)

### 방사형 계기에 니들 추가

계기 니들 또는 포인터는 계기 값을 가리키는 데 사용되며, 대부분의 최신 게이지에 사용되는 채워진 막대 디자인에 대한 대안입니다.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/4%20-Gauge-Pointers.png)

ASP.NET Core MVC용 RadialGauge 컨트롤은 이제 다음과 같은 새로운 속성과 메서드를 사용하여 니들 기반 포인터를 지원합니다.

- NeedleShape
- NeedleLength
- NeedleElement
- CreateNeedleElement

### ASP.NET Core MVC 및 웹 API에 대한 .NET Core 3.0 지원

ASP.NET Core MVC 외에도 강력한 서버 측 Web API가 .NET Core 지원 등을 통해 향상되었습니다.

- **ASP.NET Core MVC Edition 컨트롤**: 이제 Core 3.0에 대한 지원을 포함할 뿐 아니라 NuGet에서 사용할 수 있는 이러한 컨트롤의 새 버전이 제공됩니다.

- **DataEngine API**: 2019년 v2에 도입된 DataEngine API는 이제 많은 양의 데이터를 분석할 수 있습니다. 이 API는 ASP.NET Core MVC 및 Wijmo OLAP 컨트롤과 함께 사용하여 메모리 내 데이터를 고속으로 시각적으로 분석할 수 있습니다.

- **Excel API**: 이제 .NET Core 지원(베타)을 통해 이러한 API를 사용하면 XML, JSON 및 .NET 컬렉션에서 Excel 파일을 생성하고, Excel 파일을 JSON/XML로 변환하거나 그 반대로 변환하고, 파일을 분할 및 병합하며, 행과 열을 추가/제거하는 등의 작업을 수행할 수 있습니다.

- **BarCode API**: 이제 .NET Core 지원(베타)이 제공되므로 간단히 API를 호출하여 바코드를 즉석에서 생성해 보십시오. 이 API는 모든 문서에 삽입할 수 있는 바코드 이미지를 반환하며 35가지 이상의 다양한 바코드 유형을 지원합니다.

- **클라우드 저장소 API**: 이제 ASP.NET Core 지원(베타)이 제공됩니다. 이러한 클라우드 저장소 API는 Azure, AWS, DropBox, GoogleDrive 및 OneDrive 서비스를 통한 CRUD 작업을 가능하게 합니다.

<br/>

---

## 데스크탑 업데이트 - WinForms

### FlexGrid 행 세부 정보 - 계층 구조 그리드에 대한 새로운 해석

WinForms용 FlexGrid는 이미 계층 구조 데이터 트리를 지원했지만 새로운 행 세부 정보 기능을 사용하면 중첩 그리드를 생성할 때 더 유연하게 작업할 수 있습니다. 행 세부 정보를 이용하면 그리드의 각 행 아래에 있는 축소 가능 패널 내에서 추가 정보 또는 관련 정보를 표시할 수 있습니다. 입력 양식, 하위 데이터 그리드 또는 세부 정보 행에 있는 그 밖의 모든 것을 표시할 수 있습니다.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/5%20-%20FlexGrid-RowDetail.png)

FlexGrid에는 두 개의 기본 제공 행 세부 정보 공급자가 있습니다. 그중 하나인 **IC1InputPanelRowDetail**은 편집 양식으로 사용할 수 있고, 다른 하나인 **IC1FlexgridRowDetail**은 마스터 세부 정보 그리드에서 하위 레코드를 표시하는 데 사용할 수 있습니다. 또한 FlexGrid를 사용하면 사용자 정의를 통해 행 세부 정보 내의 다른 컨트롤을 보여줄 수 있습니다.

#### FlexGridRowDetail:

![ComponentOne 2019 v3](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20191120-new-release-componentone-2019v3/flexgrid.jpg)

### 공식 릴리스됨 - 훨씬 편리하고 새로운 WinForms용 리본

WinForms용 C1Ribbon 컨트롤을 처음 릴리스한 지 10년 이상이 지났습니다. 그동안 당사는 Microsoft Office와 보조를 맞추기 위해 기능을 지속적으로 추가했습니다. 올해 당사는 사용자의 요청에 부응하기 위해 새로운 리본 컨트롤을 개발할 때가 되었다고 판단했습니다. 새로운 WinForms용 리본은 .NET 4.5.2를 기반으로 구축되었으며 Office 365의 UI 개념에 기반을 두고 있습니다. 개선된 사항은 다음과 같습니다.

- 리본이 축소되었을 때 표시되는 보기가 새롭게 간소화되었습니다.
- 버튼, 진행률 표시줄, 업데이트된 갤러리 등 20개 이상의 포함된 컨트롤이 제공됩니다.
- 버튼을 위한 포함된 이미지 세트가 개선되었으며 글꼴 및 벡터 기반 아이콘에 대한 지원이 제공됩니다.
- Backstage 보기 및 상태 표시줄 컴포넌트가 제공됩니다.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/10%20-%20Ribbon-New-Beta.png)

베타 릴리스 이후로 다음과 같은 새로운 기능이 추가되었습니다.

- IconSet 속성용 디자이너
- 기본 아이콘 사전 설정의 아이콘
- C1BackstageView의 스마트 태그
- RibbonMenu 및 RibbonSplitButton 구성 요소의 PreferredItemSize 속성 이 속성은 드롭다운 항목의 크기를 지정합니다.
- 선택한 탭의 콘텐츠 스크롤 지원
- 이제 접근성을 통해 ProgressBar 값을 설정할 수 있습니다.
- DatePicker 드롭다운에 대한 접근성 지원
- RibbonColorPickerItem 클래스의 GetColorIndex 메서드 이 메서드는 팔레트에서 색상 색인을 반환합니다.
- RibbonGalleryItem 클래스의 GalleryItemTextImageRelation 속성 이 속성은 텍스트와 이미지의 위치를 각 항목에 대해 상대적으로 지정합니다.
- 리본 구성 요소의 LargeImage, Image, SmallImage 속성 이러한 속성은 클래식 버전의 리본에서 쉽게 마이그레이션할 수 있도록 추가되었습니다.

기존 리본 사용자는 새 리본이 동일한 테마를 40개 이상 지원하고 C1ThemeController를 사용하여 이 리본을 사용자 정의할 수 있다는 점에 만족하실 수 있을 것입니다. 이제 Visual Studio 도구 상자에서 "클래식"으로 표시되는 이전 C1Ribbon은 계속 유지됩니다.

[ComponentOne 행 세부 정보 사용하기](https://www.grapecity.com/blogs/getting-started-with-row-details-flexgrid-for-winforms)에 대해 자세히 알아보십시오.

### FlexPivot에서 KPI 지원

FlexPivot이 이제 데이터소스에서 추세, 목표 및 상태와 같은 KPI 정보 표시를 지원합니다. KPI 필드가 식별되면 이 필드들이 피벗 패널 내의 값 필드에 추가될 수 있습니다. FlexPivot 컨트롤에는 원통형, 계기, 표준화살표(StandardArrow), 변화량화살표(VarianceArrow), 도로표지(RoadSigns) 및 신호등(TrafficLight)과 같은 KPI를 보여주는 기본 제공 그래픽이 있습니다.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/11-FlexPivot-KPI.jpg)

### 새로운 FlexChart 디자이너로 런타임에 차트 편집

이제 WinForms용 FlexChart에 최종 사용자가 차트를 변경할 수 있도록 해주는 런타임 디자이너가 제공됩니다. 사용자는 차트의 섹션을 두 번 클릭하여 디자이너를 간단히 열 수 있습니다. 이 디자이너는 데이터 소스 필드, 계열, 축, 머리글, 바닥글, 범례 및 기타 차트 속성의 변경을 지원합니다.

##### 다음은 FlexChart 디자이너의 실제 사용 모습입니다.

<video src="/images/metalsmith/developer/componentone-enterprise/whatsnew/flexchart_designer.mp4" width="640" controls>

추가로 사용자 정의할 수 있도록 런타임 디자이너의 소스 코드가 위의 비디오에 포함된 데모와 함께 샘플로 제공됩니다. 응용 프로그램의 실행 사이에 런타임 변경 사항을 유지하기 위해 FlexChart를 직렬화할 수 있습니다. 다음은 [FlexChart 직렬화 방법](https://www.grapecity.com/samples/flexchartserializer)을 보여주는 샘플입니다.

### .NET Core 3.0에 대한 지속적인 지원

ComponentOne WinForms Edition의 전체 Studio가 .NET Core 3.0을 지원하도록 업그레이드되었습니다.

- **다중 프로젝트 템플릿 추가**: .NET Framework 디자이너의 디자이너 환경을 활용하면서 당사의 컨트롤을 사용하여 .NET Core 프로젝트를 빠르게 만들 수 있도록 해주는 .NET Core 3.0용의 새로운 다중 프로젝트 템플릿을 추가했습니다. 이 솔루션은 두 개의 프로젝트로 구성되어 있습니다. 하나는 대상 프레임워크인 .NET Core 3.0 프로젝트이고, 다른 프로젝트는 디자인을 할 수 있도록 해주는 .NET Framework 프로젝트입니다. Core 3.0 WinForms 디자이너는 아직 초기 단계이며 .NET Framework 디자이너로서 정확한 환경을 제공하지 않을 수 있으므로 이 템플릿은 개발자에게 익숙한 디자인 환경을 통해 .NET Core에서 유연하게 작업할 수 있는 방법을 제공합니다.
- **NuGet 패키지 이용 가능**: 이제 2019 v3 릴리스부터 ComponentOne WinForms Edition에는 모든 라이브러리를 위한 NuGet 패키지가 포함됩니다. 이는 NuGet을 사용하여 모든 타사 라이브러리를 관리하고자 하는 일부 개발자와 Windows Forms 응용 프로그램으로 .NET Core 3.0을 사용하는 개발자가 편리하게 이용할 수 ​​있습니다. NuGet 패키지는 Program Files/ComponentOne/WinForms Edition의 DLL과 함께 설치됩니다.

<br/>

---

## 추가 WinForms Edition 업데이트

<br/>

새로운 **C1ThemePicker** 컨트롤을 사용하면 테마 이름을 선택할 수 있고 ThemeController 속성이 설정되어 있으면 런타임에 테마를 변경할 수 있습니다.

ComponentOne WinForms Edition의 2019 v3 릴리스에는 기타 여러 가지 사소한 개선 사항이 있습니다. 이 개선 사항들은 이 게시물의 끝에 나와 있습니다.

<br/>

---

## 데스크톱 업데이트 - WPF

### ComponentOne WPF Edition .NET 업그레이드

ComponentOne WPF Edition가 .NET Framework 4.5.x 및 .NET Core 3.0을 포함한 일부 최신 기술을 지원하도록 업그레이드되었습니다.

- **새 버전은 .NET Framework 4.5.2를 대상으로 함**: WPF 컨트롤의 전체 라이브러리가 새로운 기본 버전인 .NET Framework 4.5.2로 이동되었습니다. 2019 v3 릴리스부터 WPF Edition에는 4.0과 4.5.2, 이렇게 두 개의 버전이 포함되어 있습니다. .NET 4.0은 1년정도 추가로 지원할 예정미여, 만약 사용자의 요구가 있는 경우 그보다 더 오래 지원될 예정입니다. 내년에 .NET 4.5.x 이상으로 마이그레이션할 계획이 없지만 .NET 4.0 컨트롤에 대한 추가 지원이 필요한 경우 당사에 연락해 알려주십시오.
- **.NET Core 3.0 지원**: ComponentOne WPF Edition 컨트롤은 일부 추가 절차가 있으나, .NET Core 3.0을 지원됩니다. licenses.licx 파일을 사용하는 기존 라이선싱 메커니즘은 이제 .NET Core 3.0을 대상으로 하는 새 WPF 프로젝트에서 수동으로 생성해야 합니다. 이 릴리스에는 이미 이 메커니즘이 생성되어 있는 새 프로젝트 템플릿도 포함되어 있습니다. 라이선스 파일을 수동으로 생성하는 방법에 대한 자세한 내용은 여기를 참조하십시오.

  [WPF 앱을 .NET Croe 3.0으로 마이그레이션하는 방법](https://www.grapecity.com/blogs/migrating-a-wpf-app-in-net-core-three)

- **NuGet 패키지 이용 가능**: 이제 2019 v3 릴리스부터 .NET 4.5.2 버전 전용의 전체 WPF 라이브러리도 NuGet에서 제공됩니다. .NET Core 응용 프로그램에서 WPF 컨트롤을 사용하려면 이 라이브러리가 필요합니다.

### WPF용 FlexGrid가 더 많은 열 고정 시나리오 지원

새로운 런타임 유용성 기능과 새로운 샘플은 WPF용 FlexGrid의 열 고정 및 핀 고정을 보다 효과적으로 제어할 수 있도록 하는 방법을 보여줍니다.

새로운 **AllowFreezing** 속성을 사용하면 최종 사용자도 열 고정 기능을 사용하도록 허용할 수 있습니다. 이전에는 프로그래밍 방식으로 열을 고정할 수 있었지만 이 새로운 속성 및 기능을 사용하면 열 고정을 런타임 시 완전히 사용하도록 설정할 수 있습니다.

또한 기존 API를 사용하여 **열 핀 고정**을 사용하는 방법을 보여주는 FlexGrid용 새 샘플을 추가했습니다. 열 고정(freezing)과 비슷하지만 열 핀 고정을 사용하면 더 많은 열을 왼쪽에 적절하게 고정할 수 있습니다. 사용자는 열 머리글에서 핀 아이콘을 클릭하여 열을 핀으로 고정할 수 있습니다. 핀 고정된 열은 왼쪽에서 순서가 변경되어 고정됩니다. 열 핀 고정 기능을 열 순서 변경 및 고정과 함께 결합하여 사용하면 최종 사용자가 데이터 그리드를 완전히 제어할 수 있습니다.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/12-2-FlexGrid_Pinning.png)

### WPF 행 번호용 RichTextBox

자동 행 번호를 켜면 텍스트 편집 및 수정 기능이 향상됩니다. 이제 WPF용 ComponentOne RichTextBox는 전체 문서에 걸쳐 행 번호를 연속적으로 표시하거나 각 페이지에서 1부터 다시 시작할 수 있습니다. 이 기능은 사용자가 보기 탭에서 또는 개발자가 LineNumberMode 속성을 설정하여 쉽게 전환할 수 있습니다.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/13-RichTextBox_LineNumbers1.png)

### WPF용 FlexSheet 개선 사항

- 내보낼 때 빈 셀을 제거할 수 있는 새로운 내보내기 옵션.
- 더 나은 리소스 관리로 성능이 향상되었습니다.
- 사용자는 새로운 AllowFreezing 속성을 사용하여 런타임 시 고정된 열 수를 변경할 수 없습니다.
- 메모 상자 크기가 커졌습니다.

<br/>

---

## Xamarin 업데이트

### 기본 제공 도구 모음 UI가 있는 Xamarin용 FlexViewer 릴리스

새로운 Xamarin용 FlexViewer 컨트롤을 사용하여 기본 모바일 앱에서 PDF 컨텐츠를 표시해 보십시오. FlexViewer 컨트롤은 유연한 크로스 플랫폼 보고서 및 문서 뷰어입니다. Xamarin.Forms(Android 및 iOS 전용), Xamarin.Android 및 Xamarin.iOS에서 지원되는 Xamarin 버전은 주로 PDF 파일을 표시하는 데 사용할 수 있습니다. 기본 제공 메뉴를 사용하면 런타임 검색, 인쇄 및 내보내기가 가능합니다. 이전에 Preview 버전으로 릴리스에 공개되었으며, 이번 버전에서 처음으로 공식 릴리즈 되었습니다. 이번 정식 버전에서는 사용자의 요구 사항에 맞게 UI를 사용자 정의할 수 있는 더 풍부한 API가 추가 되었습니다. 예를 들어 메뉴 항목은 쉽게 사용자 정의할 수 있으며, 전체 항목을 숨기고 자신만의 도구 모음을 사용할 수도 있습니다.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/14-FlexViewer3.png)

<br/>

---

## 서비스 구성 요소 업데이트

### 이제 C1DataEngine에 데스크톱 워크벤치 응용 프로그램 포함

Windows나 Mac에서 C1DataEngine Workbench 데스크톱 응용 프로그램을 사용하면 코드를 작성하지 않고도 직관적인 비주얼 디자이너를 사용하여 쿼리를 생성하고 시각화할 수 있습니다. 이 응용 프로그램을 데이터 분석을 위한 독립형 도구로 사용하거나, C1DataEngine을 사용하는 모든 응용 프로그램에서 생성된 기본 테이블 및 쿼리 결과를 검사하는 데 사용하십시오.

![ComponentOne 2019 v3](https://global-cdn.grapecity.com/blogs/componentone/20191120-new-release-componentone-2019v3/last-DataEngine_Workbench2.png)

.NET Core 응용 프로그램에서 C1DataEngine 라이브러리를 사용하는 개발자에게 이 도구는 다음과 같은 이점을 추가로 제공합니다.

- 코딩 없이 외부 데이터를 가져옵니다. 지원되는 데이터 형식에는 SQL Server, CSV 및 JSON이 포함됩니다.
- C1DataEngine API 라이브러리를 사용하여 프로그래밍 방식으로 쿼리를 작성하는 데 사용할 수 있는 JSON 문자열을 생성합니다.
- 다양한 차트 구성 요소를 사용하여 쿼리 결과 집합을 시각화합니다.
- 기존 C1DataEngine 작업 영역에서 원하지 않는 쿼리 결과 집합을 제거합니다.

C1DataEngine Workbench는 ComponentOne 서비스 구성 요소 모듈과 함께 설치됩니다.

### C1TextParser: PDF 및 Word 파일에서 텍스트를 구문 분석하기 위한 새로운 샘플

크로스 플랫폼 텍스트 분할 구성 요소인 C1TextParser를 지원하기 위해 PDF 및 Word 파일에서 텍스트를 추출하는 방법을 보여주는 새로운 샘플이 추가되었습니다. 이 샘플은 ComponentOne의 다른 기존 라이브러리인 C1Word 및 C1PdfDocumentSource를 활용합니다. 일반적인 사용 사례에서는 문서의 텍스트를 일반 텍스트로 읽은 다음 C1TextParser를 사용하여 일반 텍스트에서 구문 분석을 수행합니다. ComponentOne 서비스 구성 요소와 함께 설치된 Win/ExtractorEditor 샘플을 사용하여 이 기능이 작동하는 것을 확인할 수 있습니다.

<br/>

---

## 추가적인 WinForms Edition 개선 사항

<br/>

**C1Command**

- C1CommandLink 클래스에 대한 패딩(Padding) 속성을 추가했습니다.

**C1FlexGrid**

- 현재 검색 상태가 포함된 XML 문자열을 가져오거나 설정하기 위해 C1FlexGrid에 대한 SearchDefinition 속성을 추가했습니다.
- CellStyle.SearchBackColor 속성의 설명을 개선했습니다.
- C1FlexGrid에 대한 CellLabelDelay 속성을 추가했습니다. 도구 설명 레이블이 표시되기 전에 내용이 부분적으로 숨겨져 있는 셀 위에 마우스 포인터가 머무르는 시간(밀리초)을 이용하거나 설정할 수 있습니다.
- 열 필터 아이콘이 표시되는지 여부를 나타내는 ShowFilterIcon 속성을 추가했습니다.

**C1GanttView**

- C1GanttView.Options.OutlineColumn 속성을 추가했습니다.

**C1Input**

- \[C1DateEdit] 이제 다음/이전 화살표를 두 번 클릭하면 드롭다운 달력이 2개월씩 이동합니다.
- \[C1SplitButton] 드롭다운 목록에 위쪽/아래쪽 화살표 버튼을 추가했습니다. 모든 항목이 화면에 맞지 않으면 화살표가 나타납니다.

**C1InputPanel**

- InputComboBox 클래스에 ToolTipMember 속성을 추가했습니다. 이 속성은 InputComboBox 항목의 도구 설명에 속성을 가져오거나 설정합니다.

**C1List**

- HotRowChanged 이벤트를 추가했습니다.
- 마우스로 가리킨 행이 이제 HighLightRowStyle을 사용하여 강조 표시됩니다.

**C1Themes**

- 테마 적용을 제어하는 ​​데 도움이 되는 IC1Themeable 인터페이스를 추가했습니다.
- 테마가 상위 컨트롤에 적용되었는지 여부와 관계없이 테마를 하위 컨트롤에 적용하는 C1ThemeController.ApplyThemeToControlTree 메서드에 매개 변수를 추가했습니다.

**DashboardLayout**

- C1DashboardLayout.Options.HeaderAppearance 속성을 추가했습니다.

**DataFilter**

- 데이터 소스가 DataTable이고 데이터 소스가 변경될 때 CheckListFilter 항목을 업데이트하는 지원을 추가했습니다.
- C1DataFilter 컨트롤에 ShowClearFilterButtons 속성을 추가했습니다. 이 속성은 필터 머리글에 필터 지우기 버튼을 표시할지 여부를 나타내는 값을 가져오거나 설정합니다.
- Filter 클래스에 Reset 메서드를 추가했습니다. 이 메서드는 필터 값을 기본값으로 재설정합니다.
- DateRangeFilter의 날짜 편집기별로 키보드 및 마우스를 사용하는 탐색 지원을 추가했습니다.
- ChecklistFilter 항목에 대한 요약 지원을 추가했습니다.
- DataRange 필터에 대한 사용자 정의 형식 지원을 추가했습니다.
- 테마가 지정된 스크롤 막대에 대한 지원을 추가했습니다.
- AutoWidthMode 속성을 추가했습니다. 이 속성은 C1DataFilter가 자동으로 자체 너비를 설정하는 모드를 ‘가져오거나 설정합니다’.
- PredicateExpression 클래스를 추가했습니다. 이 클래스는 조건자를 필터링 함수로 사용하는 표현식을 나타냅니다. 이 클래스는 DataTable에서 작동하지 않습니다.

**FlexPivot**

- \[C1FlexPivotSlicer] 접근성 지원을 추가했습니다.
- \[C1FlexPivotChart] 최종 사용자 복사 작업에 대한 지원을 추가했습니다. Ctrl+C를 누르면 png 형식의 차트 이미지가 클립보드에 복사됩니다.

**MultiSelect**

- C1TagEditor/C1MultiSelect에서 별도의 placeholder 요소를 추가했습니다.
- \[C1CheckList] 접근성 지원을 추가했습니다.

TreeView

- 테마에서 CustomContentPresenter에 대한 그라데이션 지원을 추가했습니다.
- C1TreeView 컨트롤에 ColumnHeaderMouseClick 이벤트를 추가했습니다. 이 이벤트는 사용자가 열 머리글을 클릭할 때 발생합니다.
