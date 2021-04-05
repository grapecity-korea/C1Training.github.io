---
title: ComponentOne Enterprise 2020 V1 새로운 기능
sidebar: home_sidebar
keywords: news, blog, updates, release notes, announcements
permalink: 2019v3_whatsnew.html
folder: news
summary: "ComponentOne 2020 v1 릴리스를 새로 제공해드리게 되었음을 기쁜 마음으로 알려드립니다. 이 릴리스는 데이터에 중점을 두었습니다. 즉 온라인 데이터 소스에 연결하는 새로운 방식, 크로스 플랫폼 데이터 집합 관리, 데이터를 표시할 수 있는 새로운 UI, 데이터 분석 기능, 다양한 소스 전반에 걸친 데이터 통합 등을 제공합니다. 새롭고 강력한 .NET Standard 컴포넌트를 도입하였을 뿐 아니라 새로운 Blazor UI 컨트롤을 통한 웹 개선, ASP.NET MVC 강화, 새로운 방문자 웹 API도 포함하였습니다. 이외에도 WinForms 및 WPF 컨트롤의 기능을 향상하였습니다."
---
# ComponentOne 2020 v1의 새로운 기능

[ComponentOne](https://www.grapecity.co.kr/componentone-enterprise) 2020 v1 릴리스를 새로 제공해드리게 되었음을 기쁜 마음으로 알려드립니다. 이 릴리스는 **데이터**에 중점을 두었습니다. 즉 온라인 데이터 소스에 연결하는 새로운 방식, 크로스 플랫폼 데이터 집합 관리, 데이터를 표시할 수 있는 새로운 UI, 데이터 분석 기능, 다양한 소스 전반에 걸친 데이터 통합 등을 제공합니다.

새롭고 강력한 .NET Standard 컴포넌트를 도입하였을 뿐 아니라 새로운 Blazor UI 컨트롤을 통한 웹 개선, ASP.NET MVC 강화, 새로운 방문자 웹 API도 포함하였습니다. 이외에도 WinForms 및 WPF 컨트롤의 기능을 향상하였습니다.

## ComponentOne Blazor Edition - 첫 번째 릴리스

<br>
ComponentOne의 Blazor Edition은 나온 지 얼마 안 되었지만, 현재 개발자분께 제공할 준비를 마쳤습니다. 이 업데이트에는 버그 수정, 성능 강화, FlexGrid를 위한 새로운 필터 행 기능이 포함되어 있습니다. ComponentOne Studio Enterprise 및 Ultimate 구독 보유자는 Blazor Edition이 포함되어 있어 바로 사용해 보실 수 있습니다. 또는 개발자 라이선스를 별도로 구매하실 수 있습니다.

![필터 행](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/FlexGrid_Blazor_Filter_Row.png "Blazor 필터 행 기능")

Blazor 필터 행 기능

- [데모 보기](https://demos.componentone.com/blazor/blazorexplorer/)
- [문서 보기](https://www.grapecity.com/componentone/docs/blazor/online-blazor/filterrow.html)
- [가격 보기](https://www.grapecity.co.kr/componentone-enterprise#price)

## ComponentOne 서비스 컴포넌트 2020 v1

### .NET Standard Data Connectors로 데이터 결합

2020 v1 릴리스에서는 지원되는 다양한 데이터 소스에 대해 데이터 작업을 수행하기 위한 데이터 연결성 라이브러리의 첫 번째 버전을 제공합니다. Data Connectors는 이 첫 번째 버전에서 Dynamics 365, OData 등 인기 있는 데이터 서비스를 위한 표준 인터페이스를 제공합니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/DataConnectors.png)

이 데이터 커넥터는 ADO.NET 및 Entity Framework Core와 같은 기존 데이터 액세스 기술로 OData 또는 REST 기반 API를 통해 데이터를 노출하는 인터넷 기반 소스에 연결합니다. 이 커넥터를 당사의 다른 고유 제품인 [Data Engine](https://www.grapecity.com/data-engine)과 함께 사용하면 고성능 메모리 내 데이터 캐싱 및 분석이 가능합니다.

Data Engine 및 Data Connectors를 사용해 서로 다른 데이터 소스에 연결하고 이러한 데이터 소스에서 얻은 데이터를 병합할 수 있습니다. 또한 메모리 내 데이터 분석을 빠르게 수행하고 몇 초 내에 수백만 개의 레코드에 쿼리를 보낼 수 있습니다.

##### [자세히 알아보기](http://www.grapecity.com/componentone/net-data-connector-component)

### C1DataCollection - 새로운 .NET용 크로스 플랫폼 데이터 컴포넌트

.NET용 ComponentOne DataCollection으로 강력한 데이터 바인딩 컴포넌트를 얻으십시오. CollectionView의 표준 .NET 구현에 기반을 둔 C1DataCollection은 당사가 이전에 제공한 유용한 C1CollectionView의 크로스 플랫폼 .NET Standard 재작성입니다. C1DataCollection에서는 제공하는 것은 다음과 같습니다.

- 데이터 수집을 위한 필터링, 그룹화 및 정렬 서비스
- 큰 데이터 집합을 점진적으로 로드하기 위한 커서 및 페이징 기반 데이터 가상화
- .NET Core, WinForms, WPF, UWP, Xamarin 지원

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/services/online-datacollection/overview.html)

### Mac용 Visual Studio와 함께 ComponentOne 서비스 컴포넌트 사용

이제 새로운 Mac용 C1ControlPanel을 사용해 Mac에서 ComponentOne 서비스 컴포넌트를 설치할 수 있습니다. 액세스 권한을 얻으려면 Mac에서 다운로드하기만 하면 됩니다.

## ComponentOne WinForms Edition 2020 v1

### FilterEditor로 복잡한 필터 식 구성

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/3.jpg)

FilterEditor 컴포넌트는 DataFilter Engine을 공유하며 최종 사용자가 범주 기반 및/또는 필터 식을 쉽게 구성할 수 있도록 지원합니다. 이 컨트롤은 데이터 소스에 바인딩할 수 있으며 사용 가능한 필드에 근거하여 식을 생성할 수 있는 시각적 옵션을 자동으로 제공합니다. 복잡한 식은 AND\\OR 연산자와 사용 가능한 일련의 필터를 조합하여 생성할 수 있습니다.

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/win/online-datafilter/filtereditor.html)

### CalcEngine을 사용해 정형화된 식을 구문 분석하고 평가

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/ExcelEngine.gif)

.NET Standard용 CalcEngine으로 Microsoft Excel과 같은 식을 구문 분석하고 평가하십시오.

- 예상 매출액을 계산하거나 계산을 통해 데이터의 패턴을 파악
- Microsoft Excel에서 DataGrid로 데이터를 로드하고 계산된 값을 셀에 표시
- 대수식, 수학적 함수 및 변수를 사용하는 공식을 평가
- CrossSheet 참조 및 계산을 수행

##### [자세히 알아보기](https://www.grapecity.com/componentone/calcengine-expression-parser-component)

### WinForms용 FlexGrid의 향상된 기능

**향상된 오류 유효성 검사 기능**: FlexGrid의 유효성 검사 기능은 필수(Required), 글자수(StringLength), 범위(Range), 비교(Compare)와 같은 데이터주석(DataAnnotations)에 대한 지원 강화로 더욱 강력해졌습니다. 이외에도 편집기 값 유효성 검사를 위해 FlexGrid 열에 EditorValidation 컬렉션 속성을 추가하였습니다. 이 컬렉션에는 필수규칙(RequiredRule), 글자수규칙(StringLengthRule), 범위규칙(RangeRule), 비교규칙(CompareRule)이 포함되어 있습니다. EditorValidation 기능은 유효성 검사 시 데이터 주석을 사용하지 않는 경우에 유용합니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/4.jpg)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/win/online-flexgrid/dataannotation.html)

**데이터 가상화를 이용해 데이터를 점진적으로 로드**: 이제 FlexGrid 및 DataCollection 라이브러리를 사용해 데이터 가상화를 구현할 수 있게 되었습니다. 이 기능은 많은 양의 데이터 또는 네트워크를 경유하는 데이터를 다룰 때 유용합니다. FlexGrid는 소스에서 비동기식으로 데이터를 가져오는 VirtualDataCollection에 바인딩하는 방법으로 가용 레코드를 표시합니다. DataCollection은 다양한 구현을 통해 그룹화, 필터링, 정렬, 데이터 가상화 및 특수 시나리오를 지원하는 .NET Standard에 기반을 둔 강력한 컬렉션입니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/FlexGrid_DataVirtualization.gif)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/win/online-flexgrid/virtualdata.html)

### WinForms용 FlexPivot의 향상된 기능

**새롭고 향상된 FlexChart 차트**:: 이제 시각적 데이터 분석을 위해 새로운 FlexPivotChart 컨트롤을 이용하여 FlexPivot 내부에서 FlexCharts를 사용할 수 있게 되었습니다. FlexChart는 외관이 새롭게 바뀌었고 레거시 C1Chart 컨트롤보다 속도가 더 빠릅니다. 앞으로도 계속 FlexPivotCharts 및 FlexPivotPage를 발전시켜 데이터 분석 기능을 늘려나갈 것입니다. C1FlexPivotChart 및 C1FlexPivotPage 컨트롤은 2020 V1부터 레거시가 되지만 앞으로도 계속 이 레거시 컨트롤을 유지할 것입니다. 다행히도 사용자 정의 코드가 없다면, 기존에 상용하셨던 C1FlexPivotChart를 쉽고 빠르게 새 FlexCharts로 쉽게 변환할 수 있습니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/5.jpg)

**TopN 및 BottomN 필터로 향상된 데이터 분석 기능**: 사용자는 TopN 필터를 이용해 데이터에서 선행 및 후행 요소를 검색할 수 있습니다. 예를 들어 이 필터를 사용해 상위 10개의 작동 제품 또는 하위 20개의 후행 판매 지역을 검색할 수 있습니다. 이 기능은 최종 사용자가 런타임에 조회 필터 필드 설정을 통해 사용할 수 있습니다. 필터는 필드의 필터 속성에 프로그래밍 방식으로 적용할 수 있습니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/6.jpg)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/win/online-flexpivot/top-n-filter.html)

## ComponentOne WPF Edition 2020 v1

### 새로운 WPF용 DataFilter 컨트롤

새로운 WPF용 DataFilter 컨트롤은 슬라이서와 지능적인 필터 UI를 조합한 것입니다. 이 컨트롤은 동일한 WinForms에 기반을 두고 있으며 이 컨트롤을 이용해 사용자는 여러 가지 조건에 따라 데이터를 필터링할 수 있습니다. 이 컨트롤은 DataGrid, 목록, TreeView, 차트, 맵과 같은 데이터 인식 컨트롤 또는 모델과 바인딩할 수 있습니다. 대시보드 응용 프로그램에서 DataFilter를 사용하여 Amazon에서 볼 수 있는 친숙한 전자 상거래 필터 패널에서 데이터를 분리할 수 있습니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/7.jpg)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/wpf/online-datafilter/overview.html)

## ComponentOne ASP.NET Core 및 MVC Edition 2020 v1

### FileManager UI를 사용해 클라우드에서 파일 관리

새로운 FileManager UI 컨트롤은 당사의 클라우드 저장소 Web API와 통합되어 여러 파일에 대한 CRUD 작업용 인터페이스를 제공합니다. Web API는 Azure, Amazon Web Services(AWS), DropBox, GoogleDrive, OneDrive와 같은 클라우드 저장소 서비스를 지원합니다. 컨트롤의 직관적인 UI는 Windows 파일 탐색기와 비슷하며, 메뉴를 통해 손쉽게 파일을 나열, 검색, 이동, 업로드, 삭제, 다운로드할 수 있게 지원합니다. 이 컨트롤은 ASP.NET MVC 및 ASP.NET Core MVC에서 사용할 수 있습니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/8.png)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/file-manager.html)

### 뒤바뀐 그리드를 사용하는 새로운 그리드 관점

TransposedGrid는 FlexGrid 컨트롤을 확장한 것으로서, 뒤바뀐 레이아웃을 사용하여 열은 데이터 항목으로, 행은 항목 속성으로 표시합니다. 뒤바뀐 레이아웃은 각 항목에 여러 가지 속성이 있는 경우 항목을 서로 비교하거나 몇 가지 데이터 항목을 표시할 때 유용합니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/9.jpg)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/transposed-grid.html)

### ASP.NET Core MVC용 FlexGrid의 향상된 기능

**실용성이 탁월한 전체 텍스트 검색**: 그리드의 모든 열에 대해 한꺼번에 필터 적용 검색을 수행합니다. 이 기능에는 강조 표시된 일치 항목에 대한 CSS 스타일 지정도 포함되어 있습니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/10.png)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/full-text-search.html)

**열 고정**: 열 고정 기능을 통해 최종 사용자는 단순히 “핀을 꽂는” 방식으로 열을 이동하고 고정할 수 있습니다. 이처럼 간단한 사용 편의성 향상은 기존 스크롤 방식에 불편함을 느낀 다수의 최종 사용자가 요청한 부분입니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/colum-pinning.png)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/pinning-column.html)

**템플릿으로 셀을 사용자 정의**: 이제 FlexGrid의 열은 사용자 정의 콘텐츠를 지원하는 템플릿 속성을 갖게 되었습니다. 아래 그리드의 금액 열에서는 HTML을 사용해 값에 따라 셀의 색상을 표시합니다. 템플릿 기능은 열 셀에 임의 HTML 콘텐츠를 표시하는 데 사용할 수 있습니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/12.png)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/CustomCellTemplate.html)

**여러 열 정렬 기능 새로 추가**: 이제 ASP.NET Core MVC용 FlexGrid는 열 헤더를 클릭하여 여러 열을 정렬하는 기능을 지원합니다. 이 기능은 간단히 구현할 수 있습니다. AllowSorting 열거 속성에 새로운 MultiColumn 열거 기능이 도입되어 그리드를 여러 열에 정렬할 수 있게 되었습니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/13.png)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/flexgridkeyfeatures.html)

**축소 가능한 열 그룹**: FlexGrid를 사용해 계층 구조 열 헤더를 생성할 수 있습니다. 2020 v1 릴리스에서는 이 열 그룹을 축소하여 UI를 최소화할 수 있습니다.
![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/14.jpg)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/column-group.html)

### ASP.NET Core MVC용 MultiRow의 향상된 기능

**MultiRow 그룹 헤더**: MultiRow 그룹 헤더를 사용해 그룹 헤더에 헤더 행이 하나가 아닌 여러 개 있어야 하는지 판단할 수 있습니다. 이 기능은 그룹 헤더에 집계 값을 표시할 때 유용합니다.

![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/15.png)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/KeyFeaturesMultiRow.html)

**헤더 레이아웃 정의** 기본적으로 MultiRow 컨트롤에서는 열 헤더와 셀 데이터에 대해 동일한 레이아웃 정의를 사용합니다. 새로운 headerLayoutDefinition 속성을 사용하여 열 헤더의 레이아웃을 사용자 정의할 수 있습니다.
![](https://gccontent.blob.core.windows.net/gccontent/blogs/componentone/20200403-componentone-2020-v1-release/16.jpg)

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/mvc/online-mvc/LayoutDefinition.html)

## Web API 향상된 기능 2020 v1

### 새로운 방문자(Visitor) Web API

새로운 .NET Core 방문자 Web API는 IP, 지리적 위치, 언어, 참조 사이트, 세션, 운영 체제, 장치, 브라우저와 같은 사용자 데이터를 수집합니다. 이 Web API는 웹 개발자가 개별 사용자에게 콘텐츠를 사용자 정의하는 데 유용합니다.

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/webapi/online-webapi/visitor-api.html) | [데모 보기](https://demos.componentone.com/aspnet/5/webapiexplorer/Visitor)

### 모든 Web API에 대한 .NET Core 지원

ComponentOne은 2019 v3에서 Excel, BarCode, DataEngine, 클라우드 저장소를 위한 .NET Core Web API를 베타 버전으로 도입하였습니다. 2020 v1에서는 이 Web API가 베타 버전에서 벗어나 .NET Core 2.0 이상을 지원합니다. 또한 WinForms, JavaScript(TypeScript 사용) 및 MVC 응용 프로그램에서 이 API를 사용하는 방법을 보여주는 여러 가지 플랫폼 샘플을 추가하였습니다.

게다가 이제는 새로운 Mac용 C1ControlPanel을 사용해 Mac에서 ComponentOne Web API 컴포넌트를 설치할 수 있습니다.

## Xamarin의 향상된 기능 2020 v1

### FlexGrid 필터 행

Xamarin.Forms, iOS 및 Android용 FlexGrid는 이제 클래식 필터 행 기능을 지원합니다. 필터 행은 그리드 상단에 있는 정적 행으로서 사용자는 이를 이용해 열을 기준으로 필터링을 할 수 있습니다.

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/xamarin/online-forms/filter-row.html)

### FlexViewer 내보내기

FlexViewer는 햄버거 메뉴의 몇 가지 향상된 기능을 통해 모바일이 기능을 강화하였습니다. 이제 사용자는 햄버거 메뉴에서 직접 문서를 인쇄하고 내보낼 수 있습니다. 게다가 밝은 테마와 어두운 테마를 지원하는 기능이 있어 iOS 및 Android용 새 어두운 테마를 이용할 때 메뉴가 기본적으로 멋지게 스타일 지정됩니다.

##### [자세히 알아보기](https://www.grapecity.com/componentone/docs/xamarin/online-forms/hamburger-menu.html)

또한 이제는 새로운 Mac용 C1ControlPanel을 사용해 Mac에서 Xamarin용 ComponentOne Studio 컴포넌트를 설치할 수 있습니다.
