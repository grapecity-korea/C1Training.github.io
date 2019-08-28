---
title: ComponentOne for ASP.NET | UI
keywords: ComponentOne, ASP.NET, ui
last_updated: Aug 08, 2019
summary: "ComponentOne for ASP.NET 가 제공하는 UI 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1asp_ui.html
folder: mydoc
---


## C1Dialog대화창 만들기

ASP.NET Wijmo의 C1Dialog 컨트롤은 대화창을 만들 수 있습니다. 이런 특수한 유형의 대화창을 클라이언트에 만들 수 있습니다. 또는 서버에 메시지를 표시하고 고객의 입력한 내용을 접수할 수 있습니다.  
이 예시는 기본  C1Dialog컨트롤을 표시합니다. 이 컨트롤로 에러, 설명 등의 메시지를 표시할 수 있습니다. 대화창은 이동시키거나 크기를 변경하거나 'X'아이콘으로 닫을 수 있습니다.

  

C1Dialog컨트롤을 페이지에 추가하기

대화창 설정

C1Dialog.Title을 사용하여 대화창의 타이틀을 설정합니다.

C1Dialog.Content태그를 사용하여 대화창의 내용을 설정합니다. 에러, 설명 등의 메시지를 표시할 수 있습니다.

코드는 다음과 같습니다.

  

```csharp
<cc1:C1Dialog ID="dialog" runat="server" Width="550px" Height="240px" Title="서베이">
    <Content>
        <h2>대화창</h2>
    </Content>
</cc1:C1Dialog>
```

페이지에 대화창표시와 대화창 감추기의 버튼 두 개를 추가합니다. 코드는 다음과 같습니다. ：

```csharp
<input type="button" value="대화창감추기" onclick="$('#<%=dialog.ClientID%>').c1dialog('close')" />
  
<input type="button" value="대화창표시" onclick="$('#<%=dialog.ClientID%>').c1dialog('open')" />
```

페이지 로드하면 다음과 같은 페이지가 표시됩니다. 감추기 버튼을 클릭하면 대화창이 감춰집니다. 대화창 표시 버튼을 클릭하면 대화창이 나타납니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc5-1-1.png)

본문 Demo의 소스코드는 다음과 같습니다. :

[C1Dialog-overview.zip](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1Dialog-overview.zip)


## C1Rating컨트롤 애니메이션 설정방법

ASP.NET의Rating컨트롤은 도형을 통해 ASP.NET에 등급을 표시할 수 있습니다. 해당 등급 컨트롤은 웹 사이트 방문자들이 투표를 통해 그들의 의견을 공유할 수 있도록 합니다. 해당 컨트롤을 사용자 정의 할 수 있으며, 별표, 엄지손가락, 막대그래프 등으로 등급을 표시할 수 있습니다.

본문에서는C1Rating 애니메이션을 어떻게 설정하는지 소개합니다.

구체적인 방법은 다음과 같습니다.

  

### C1Rating컨트롤 페이지 추가하기

C1Rating 등급 컨트롤을 페이지에 수평이나 수직으로 놓을 수 있습니다.

  

### C1Rating사용자 정의 아이콘

기본적으로 별표로 표시되며 사용자 정의를 통해 다른 아이콘으로도 등급 컨트롤을 만들 수 있습니다.

  

### C1Rating애니메이션

ComponentOne등급 컨트롤에 특수효과를 추가할 수 있습니다. 등급 컨트롤이 스크롤, 팝업, 페이딩, 슬라이드 등으로 전환되도록 설정할 수 있습니다. 애니메이션 효과를 설정하는 태그는 Animation입니다. 코드는 다음과 같습니다. :

  

```csharp
<Animation Animated="fade" Duration="500" Easing="Linear" Delay="250" />
```

### C1Rating알림

C1Rating에 마우스를 가져다 놓으면 메시지 알림이 나타납니다. 메시지 알림용 Hint태그를 설정합니다. 코드는 다음과 같습니다. :

  

```csharp
<Hint Content="Below Average,Average,Above Average,Awesome,Epic" />
```

마우스를 페이지의 C1Rating에 놓으면 메시지 알림이 나타납니다. 마우스로 별 아이콘을 클릭하면 별 등급을 설정할 수 있게 됩니다. 다음 그림과 같이 표시됩니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc5-2-1.gif)

본문 Demo의 소스코드는 아래와 같습니다. :

[C1Rating.zip](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestGauge.zip)