---
title: ComponentOne for ASP.NET | 데이터 상호작용
keywords: ComponentOne, ASP.NET, 웹폼, 데이터 상호작용
last_updated: Aug 08, 2019
summary: "ComponentOne for ASP.NET 이 제공하는 내비게이션 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1asp_dataInteraction.html
folder: mydoc
---


## C1GridView 데이터 운영

C1GridView는 순서배열, 필터, 페이지 분류 및 그룹 나누기 등 실용적인 기능을 많이 가지고 있습니다. 간단한 속성설정만 하면 이런 기능들의 실현이 가능하고, 개발인력의 시간 소모를 대폭 절감할 수 있습니다.

C1GridView는 설계 시 상기 기능을 간단하게 실현할 수 있습니다. 상응하는 속성을 true로 설정하기만 하면 됩니다. 단, 일부 개발자의 경우 사용 시 데이터 바인딩을 하고 다시 이런 기능들을 실현시켜야 하는 경우도 있습니다.

본문에서는 데이터 소스의 동적 바인딩 시 코드를 통해 이상의 기능들을 어떻게 실현하는지 토론하고자 합니다.

  

C1GridView 바인딩

C1GridView는 DataSet，DataTable 등과 같은 ADO.NET 데이터소스를 바인딩 할 수 있습니다. 아래는 ‘Customers’ 데이터 표를 C1GridView의 코드에 바인딩 한 것입니다.

  

```csharp
public DataSet BindGrid()
{
    OleDbConnection con = new OleDbConnection("provider=Microsoft.Jet.Oledb.4.0; Data Source=" + Server.MapPath("~/App_Data/C1NWind.mdb"));
    OleDbDataAdapter da;
    DataSet ds = new DataSet();
    da = new OleDbDataAdapter("Select * from Customers", con);
    da.Fill(ds);
    return ds;
 }
  
protected void Page_Load(object sender, EventArgs e)
{
    if (!IsPostBack)
    {
        C1GridView1.DataSource = BindGrid();
        C1GridView1.DataBind();
    }
}
```

### C1GridView 이벤트 오퍼레이팅
[C1GridView 이벤트 오퍼레이팅 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/GridViewOperation.zip)
**Sort**

순서배열기능은  Sorting과  Sorted  이벤트를 오퍼레이팅하고 Sorted 이벤트에서 새롭게 데이터 소스를 바인딩해야 실현됩니다.

```csharp
protected void C1GridView1_Sorting(object sender, C1.Web.Wijmo.Controls.C1GridView.C1GridViewSortEventArgs e)
{
}
//Handles Sorting
protected void C1GridView1_Sorted(object sender, EventArgs e)
{
    C1GridView1.DataSource = BindGrid();
    C1GridView1.DataBind();
}
```

**필터**

필터 기능은  Filtering과  Filtered  이벤트를 오퍼레이팅하고  Filtered  이벤트에서 새롭게 데이터 소스를 바인딩해야 실현됩니다.

```csharp
protected void C1GridView1_Filtering(object sender, C1.Web.Wijmo.Controls.C1GridView.C1GridViewFilterEventArgs e)
{
}
//Handles Filtering
protected void C1GridView1_Filtered(object sender, EventArgs e)
{
    C1GridView1.DataSource = BindGrid();
    C1GridView1.DataBind();
}
```

**페이지 나누기**

페이지 나누기의 코드와 순서배열, 필터는 약간 다릅니다.  Paging  이벤트를 실행해야 합니다. 먼저, NewPageIndex 속성을 현재의 PageIndex로 설정함과 동시에 데이터 소스를 새롭게 바인딩해야 합니다.

```csharp
protected void C1GridView1_PageIndexChanging(object sender, C1.Web.Wijmo.Controls.C1GridView.C1GridViewPageEventArgs e)
{
    C1GridView1.PageIndex = e.NewPageIndex;
    C1GridView1.DataSource = BindGrid();
    C1GridView1.DataBind();
}
```

**그룹 나누기**

C1GridView의 그룹나누기 기능은 AllowColMoving 과 ShowGroupArea 속성을 true로 설정합니다. ColumnGrouped 와 ColumnUngrouped 이벤트를 실행해야 합니다. ColumnGrouped 이벤트에서는 이벤트 변수를 통해 데이터소스를 다시 바인딩해야 합니다. 매개 변수인 HeaderText 속성은 드래그한 열의 헤드 텍스트입니다. 이 매개 변수는 먼저 열을 정렬 한 다음 그룹화하여 중복 된 그룹화를 피할 수 있습니다.

```csharp
//그룹나누기 실행
protected void C1GridView1_ColumnGrouped(object sender,   C1.Web.Wijmo.Controls.C1GridView.C1GridViewColumnGroupedEventArgs e)
{
    C1GridView1.DataSource = BindGrid(e.Drag.HeaderText);
    C1GridView1.DataBind();
}

//그룹나누기 취소
protected void C1GridView1_ColumnUngrouped(object sender, C1.Web.Wijmo.Controls.C1GridView.C1GridViewColumnUngroupedEventArgs e)
{
}
```

더 많은 C1GridView 표 양식 컨트롤 관련 정보는，다음을 참고해 주시기 바랍니다. ：

[C1GridView 이벤트 오퍼레이팅 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/GridViewOperation.zip)


## C1GridView 정렬이 가능한 표 양식 만들기

본문은 정렬이 가능한 표 양식을 간단하게 시연합니다. C1GridViewfh로 데이터 소스를 바인딩합니다. 표 양식의 열은 데이터 소스의 필드 명을 표시하며, 행은 데이터 소스의 실 데이터를 나타내도록 합니다. 아래에서 코드를 통해 어떻게 기능들을 구현하는지 소개합니다.

먼저, ASP.NET 공정에 C1GridView 컨트롤을 추가해줍니다. 그리고 정렬이 가능한 바인딩 표 양식을 만듭니다.

  

### 데이터 소스 추가

표 양식에 Sql데이터 소스를 추가합니다. 아래의 코드는”Employ” 데이터소스 표를 sql데이터소스에서 추가하여 넣은 것입니다.

  

```csharp
<asp:SqlDataSource ID="SqlDataSource1" runat="server" ConnectionString="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=|DataDirectory|\C1Nwind.mdb;Persist Security Info=True" ProviderName="System.Data.OleDb" SelectCommand="SELECT [EmployeeID], [LastName], [FirstName], [BirthDate] FROM [Employees]">
</asp:SqlDataSource>
```

### C1GridView 이벤트 오퍼레이팅

[C1GridView 이벤트 오퍼레이팅 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1GridView-overview.zip)

C1GridView의 DataSourceID 속성으로 데이터 소스를 바인딩 하고 아래의 DataField 속성을 구체적인 데이터소스 영역에 지정합니다. C1GridView 표 양식의 행은 데이터 소스의 모든 기록을 표시합니다.

구체적인 코드는 다음과 같습니다. :

```csharp
<wijmo:C1GridView ID="C1GridView1" runat="server" DataSourceID="SqlDataSource1" 
    AutoGenerateColumns="false" ShowRowHeader="true" AllowSorting="true" CallbackSettings-Action="All"> 
    <Columns> 
        <wijmo:C1BoundField HeaderText="ID" DataField="EmployeeID" SortExpression="EmployeeID" /> 
        <wijmo:C1BoundField HeaderText="Last name" DataField="LastName" SortExpression="LastName" /> 
        <wijmo:C1BoundField HeaderText="First name" DataField="FirstName" SortExpression="FirstName" />
        <wijmo:C1BoundField HeaderText="Date of birth" DataField="BirthDate" DataFormatString="d" SortExpression="BirthDate" />
    </Columns>
</wijmo:C1GridVie>
```

실행하면 다음 그림과 같은 결과를 얻을 수 있습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc3-2-1.png)

  

본문의 Demo는 다음과 같습니다. :

[C1GridView 이벤트 오퍼레이팅 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1GridView-overview.zip)



## GridView 컨트롤 그룹핑

ASP.NET Wijmo의GridView 컨트롤은 하나의 데이터소스로부터 표시하는 항목을 지원할 수 있고 선택, 편집, 삭제, 배열 및 그룹 데이터의 조정을 가능하게 합니다. 본문은 하나의 데이터소스로부터 어떻게 항목을 표시하는지, 또한 지정위치에 드래그 된 열에 따라 그룹을 나누고 그룹 헤드의 접기와 펼치기가 가능한지, 해당 표 양식이 각 그룹의 헤드라인 옆에서 접거나 펼쳐서 표시되는지 소개합니다. 예를 들어 수량이나 금액 같은 요약 데이터를 그룹 나누기 행에서 표시할 수 있습니다.

구체적인 방법은 다음과 같습니다.

  

### 데이터 소스바인딩

C1GridView컨트롤을 페이지에 드래그하고 데이터소스를 설정합니다.

  

```csharp
<asp:sqldatasource id="SqlDataSource1" runat="server" connectionstring="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=|DataDirectory|\C1NWind.mdb;Persist Security Info=True" providername="System.Data.OleDb" selectcommand="SELECT TOP 50 Products.ProductName, d.OrderID, d.Quantity, (d.UnitPrice * d.Quantity) as Total FROM Products INNER JOIN (SELECT details.ProductID, details.OrderID, details.UnitPrice, details.Quantity FROM [Order Details] AS details INNER JOIN (SELECT OrderID FROM Orders WHERE Year(OrderDate) = 1994) AS tmp ON details.OrderID = tmp.OrderID) as d ON Products.ProductID = d.ProductID ORDER BY d.ProductID"> 
</asp:sqldatasource>
```

C1GridView은 DataSourceID를 통해 데이터소스를 선택하고 Columns의 DataField는 데이터소스의 영역을 선택합니다.

  

### 그룹나눔
[C1 GridView 컨트롤 그룹핑 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1GridView-Grouping.zip)

그룹 헤드와 마지막 행은  wijmo-wijgrid-groupheaderrow와  wijmo wijgrid-groupfooterrow  CSS유형으로 표기합니다. 개발자는 이 유형들과 Child Node를 결합 사용하여 그룹 행의 자체정의 양식을 제공하도록 합니다. 그룹 나눔을 실현하는 코드는 다음과 같습니다. ：

```csharp
<wijmo:C1BoundField DataField="ProductName" SortExpression="ProductName" HeaderText="제품명" Aggregate="Count"> 
    <GroupInfo Position="Header" OutlineMode="StartCollapsed" />
</wijmo:C1BoundField> 
<wijmo:C1BoundField DataField="OrderID" SortExpression="OrderID" HeaderText="주문서ID"></wijmo:C1BoundField> 
    <wijmo:C1BoundField DataField="Quantity" SortExpression="Quantity" HeaderText="수량" Aggregate="Sum"></wijmo:C1BoundField> 
    <wijmo:C1BoundField DataField="Total" SortExpression="Total" HeaderText="총계" Aggregate="Sum"></wijmo:C1BoundField>
    </Columns> 
</wijmo:C1GridView>
```

본문의 Demo에서 C1GridView의 AllowColMoving를 통해 true가 허용한 드래그 열을 설정하게 됩니다. 그룹 헤드 유닛 셀은  wijmo-wijgrid.TD wijmo wijgrid-groupheaderrow  CSS 서열로 설계됩니다. 또한 제품명을 그룹으로 나눕니다. 그룹으로 나눈 후 그룹 헤드에서 제품명과 수량의 요약데이터를 표시합니다. OutlineMode을 통해 설정된 StartCollaspsed가 나타내는 그룹에서 가장 최초의 그룹은 모두 접혀 있습니다.  
페이지에서 표시된 후 그룹 헤드의 도표를 클릭하면 그룹을 펼치거나 접을 수 있습니다.  
해당 Demo를 실행하면 다음과 같이 표시됩니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc3-3-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

[C1 GridView 컨트롤 그룹핑 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1GridView-Grouping.zip)



## 데이터를 C1EventsCalendar 에 바인딩시키는 방법
[C1 이벤트 캘린더 데이터 바인딩 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1EventsCalendar-Databinding.zip)

본문에서는C1EventsCalendar컨트롤을 통한 통합기능 스케줄러 응용프로그램의 제작을 소개합니다. 일일, 일주일, 근무주간이나 매월의 도표로 공유캘린더와 개인 캘린더를 표시하고 데이터 소스에 바인딩되거나 내장된 데이터소스로 데이터를 보존하고 추가 로드할 수 있습니다.  
본문에 첨부된 Demo를 통해 어떻게 데이터를 C1EventsCalendar 컨트롤에 바인딩시키는지 확인할 수 있습니다.

C1EventsCalendar를 한 데이터 소스에 바인딩시키려면 아래의 몇 가지 C1EventsCalendar 방법이 필요합니다. ：

  

### 시간설정저장

페이지에 데이터소스 컨트롤 AccessDataSource를 추가합니다.

C1EventsCalendar일정을 저장한 DataSourceID속성을 설정합니다. 필요하다면 DataMember속성을 기입합니다.

최종사용자가 일정을 편집하여 삽입/업데이트/삭제명령을 생성하도록 합니다. 다음과 같이 표시합니다. :

  

```csharp
DeleteCommand="DELETE FROM [Appointments] WHERE [AppointmentId] = ?" 
InsertCommand="INSERT INTO [Appointments] ([AppointmentId], [Description], [End], [Location], [Start], [Subject], [Properties], [Color], [Calendar], [Tag]) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?)" 
SelectCommand="SELECT * FROM [Appointments]" 
UpdateCommand="UPDATE [Appointments] SET [Description] = ?, [End] = ?, [Location] = ?, [Start] = ?, [Subject] = ?, [Properties] = ?, [Color] = ?, [Calendar] = ?, [Tag] = ? WHERE [AppointmentId] = ?"
```

설정한C1EventCalendar일정은 저장 데이터를 반영합니다. 다음과 같은 코드로 표시합니다. :

```csharp
<EventStorage DataSourceID="AccessDataSource_Events">
	<Mappings>	
		<IdMapping MappingName="AppointmentId" />			
		<StartMapping MappingName="Start" />
		<EndMapping MappingName="End" />
		<SubjectMapping MappingName="Subject" />
		<LocationMapping MappingName="Location" />
		<DescriptionMapping MappingName="Description" />
		<ColorMapping MappingName="Color" />
	</Mappings>
</EventStorage>
```

### CalendarStorage를 설정합니다.

페이지에 데이터소스 AccessDataSource를 추가합니다.

C1EventsCalendar일정에 저장된 DataSourceID속성을 설정합니다. 필요한 경우, DataMember속성을 기입합니다.

최종 사용자가 일정을 편집하여 삽입/업데이트/삭제명령을 생성하도록 합니다.

설정한C1EventCalendar일정은 저장 데이터를 반영합니다. 예：

```csharp
<CalendarStorage DataSourceID="AccessDataSource_Calendars">
	<Mappings>
		<IdMapping MappingName="CalendarId" />
		<LocationMapping MappingName="Location" />
		<ColorMapping MappingName="Color" />
		<DescriptionMapping MappingName="Description" />
		<NameMapping MappingName="Name" />
		<PropertiesMapping MappingName="Properties" />
		<TagMapping MappingName="Tag" />
</Mappings>
</CalendarStorage>
```

페이지를 추가하면 다음과 같은 결과를 얻을 수 있습니다. 일자, 주, 월 및 근무주의 도표를 변경할 수 있고 알림, 태그 및 사용가능상태를 사용하여 한 번, 일일 또는 매년 정기약속으로 계획을 작성할 수 있으며 종류별, 자료 및 담당자 별로 조직적이고 일관성 있게 유지할 수 있습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc3-4-1.gif)

  

본문 Demo의 소스코드는 다음과 같습니다. :

[C1 이벤트 캘린더 데이터 바인딩 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1EventsCalendar-Databinding.zip)


## C1EventCalendar 컨트롤 입문

[C1 이벤트 캘린더 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestEventCalendar.zip)

C1EventCalendar 컨트롤을 사용하여 iPad의 캘린더 응용프로그램과 유사한 디자인의 통합기능 스케줄 관리 응용프로그램을 만들 수 있습니다. 일일, 일주일, 근무주간 또는 매월의 도표로 공유 캘린더와 개인 캘린더를 표시하고 데이터 소스에 바인딩되거나 내장된 데이터소스로 데이터를 저장하고 추가 로드할 수 있습니다. 아래의 방법으로 고급 컨트롤을 사용할 수 있습니다.

  

**Step1**

먼저,  ASP.Net Web응용프로그램을 만든 후,  Web 폼을 추가합니다. 그리고 툴 바에서  C1EventCalendar 컨트롤을 찾습니다. 툴 바에 C1EventCalendar가 없는 경우, 오른쪽을 클릭하여 “선택옵션”을 선택하고 C1EventCalendar를 추가합니다.

  

**Step2**

C1EventCalendar컨트롤을 더블클릭하고 페이지에 추가합니다. 컨트롤의 테스크 메뉴를 열어 너비와 높이를 각각 800과 500으로 설정합니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc3-5-1.png)

EventCalendar컨트롤의 속성을 설정하여 컨트롤을 일부 변경합니다. TimeInterval의 값은 60으로, TimeIntervalHeight의 값은 25로, TimeRulerInterval의 값은 60으로 설정합니다. 이 속성들은 분(min)을 단위로 합니다.

![](https://www.grapecity.co.kr/images/training/c1/tc3-5-2.png)

EventCalendar의 Theme양식을 변경할 수 있습니다. 컨트롤의 테스크 메뉴를 열면 Theme옵션을 볼 수 있습니다. Rocket Theme를 선택합니다.

  

**Step3**

간단한 일정 캘린더가 완성되었습니다. 실행하면 다음과 같이 표시됩니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc3-5-3.png)

Web페이지에서 직접 스케줄을 추가할 수 있습니다.

![](https://www.grapecity.co.kr/images/training/c1/tc3-5-4.png)

  

물론, 데이터 바인딩을 통해 스케줄을 추가할 수 있습니다.

[C1 이벤트 캘린더 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestEventCalendar.zip)



## C1Input입력 컨트롤

ASP.NET의Input 컨트롤은 내장된 마스크, 사용자 정의 서식 지원, 지역화 등을 가져올 수 있습니다. 본문은 마스크, 날짜, 숫자 및 사용자 지정 편집을 포함하는 입력 컨트롤에 대해 설명합니다.

  

### C1Input입력 컨트롤 페이지 추가

[C1 Input 컨트롤 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1Input.zip)

입력컨트롤 개요

페이지에 데이터소스 컨트롤 AccessDataSource를 추가합니다.

C1EventsCalendar일정을 저장한 DataSourceID속성을 설정합니다. 필요하다면 DataMember속성을 기입합니다.

C1InputCurrency는 C1InputNumeric에서 파생됩니다. 화폐 값을 입력하는데 사용됩니다. 디지털 편집기를 사용하면 사용자 지정 유효성 검사 논리를 작성하지 않고도 응용 프로그램에서 입력을 지정할 수 있습니다.  
참고 코드는 다음과 같습니다. ；

```csharp
<wijmo:C1InputCurrency ID="C1InputCurrency" runat="server" Value="123.45">
</wijmo:C1InputCurrency>
```

C1InputDate는 C1InputMask에서 파생되어 일자와 시간을 입력하는 데 사용됩니다. C1DateInput컨트롤은 일자 에디터를 제공합니다.

C1InputMask  의 컨트롤은 주로 텍스트 양식에 관련된 데이터 유형 정보를 입력하고 편집하는 데 사용되는 Web 네트워크 컨트롤입니다. 데이터 양식, 마스크 편집, 데이터 검증 및 기타 기능을 지원할 수 있습니다. 또한 추가 기능을 포함하여 모든 데이터유형의 양식화와 편집차단을 지원할 수 있습니다. 주요 데이터 에디터 컨트롤 외에는 C1InputMask도 전문 컨트롤로서 C1InputDate컨트롤과 C1InputNumeric컨트롤처럼 기본유형이 있습니다.

C1InputNumeric은 C1InputMask에서 파생된 것으로 숫자 입력에 사용됩니다. 해당 디지털 에디터를 사용하여 응용프로그램에서 입력을 지정할 수 있어 어떤 사용자 지정 유효성 검사 논리를 작성하지 않고도 응용 프로그램에서 입력을 지정할 수 있습니다. 참고 코드는 다음과 같습니다. :

```csharp
<wijmo:C1InputNumeric ID="C1InputNumeric1" runat="server" 
ShowSpinner="true" value="2.324" DecimalPlaces="3">
</wijmo:C1InputNumeric>
```

C1InputPercent  는 C1InputNumeric에서 파생된 것으로 백분율 입력에 사용됩니다. 해당 디지털 에디터를 사용하여 응용프로그램에서 입력을 지정할 수 있어 어떤 사용자 지정 유효성 검사 논리를 작성하지 않고도 응용 프로그램에서 입력을 지정할 수 있습니다.

  

C1Input의 모든 입력 컨트롤을 페이지에 추가합니다. 결과는 다음과 같습니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc3-6-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

[C1 Input 컨트롤 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1Input.zip)



## C1ComboBox애니메이션 효과 표시

[C1 ComboBox 애니메이션 효과 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1ComboBox-animation.zip)

ASP.NET의 C1ComboBox는 편집 가능한 텍스트 상자와 드롭 다운 리스트를 함께 결합하여 자동으로 검색할 수 있습니다. Items속성 설정을 통해 사용자는 C1ComboBox의 외관과 드롭 다운 메뉴 리스트 항목을 제어할 수 있습니다. 드롭 다운 메뉴를 표시하거나 숨길 때, C1ComboBox는 애니메이션 효과를 표시할 수 있습니다.  
구체적인 방법은 다음과 같습니다.

  

C1ComboBox를 페이지에 추가합니다.

드롭 다운 메뉴 리스트 항목을 설정합니다.

Items  속성의 설정을 통해  C1ComboBox의 외관과 드롭 다운 메뉴 리스트 항목을 제어할 수 있습니다. 코드는 다음과 같습니다. :

```csharp
<Items>
<wijmo:C1ComboBoxItem Text="c++" Value="c++" />
<wijmo:C1ComboBoxItem Text="java" Value="java" />
<wijmo:C1ComboBoxItem Text="php" Value="php" />
<wijmo:C1ComboBoxItem Text="coldfusion" Value="coldfusion" />
<wijmo:C1ComboBoxItem Text="javascript" Value="javascript" />
<wijmo:C1ComboBoxItem Text="asp" Value="asp" />
<wijmo:C1ComboBoxItem Text="ruby" Value="ruby" />
<wijmo:C1ComboBoxItem Text="python" Value="python" />
<wijmo:C1ComboBoxItem Text="c" Value="c" />
<wijmo:C1ComboBoxItem Text="scala" Value="scala" />
<wijmo:C1ComboBoxItem Text="groovy" Value="groovy" />
<wijmo:C1ComboBoxItem Text="haskell" Value="haskell" />
<wijmo:C1ComboBoxItem Text="perl" Value="perl" />
</Items>
```

애니메이션 효과 설정

애니메이션을 표시하거나 숨기려면 다음 옵션으로 설정합니다. :

• ShowingAnimation  - 드롭 다운 메뉴가 보일 때 효과가 나타납니다.

• HidingAnimation  - 드롭 다운 메뉴를 숨길 때 효과가 나타납니다.

ShowingAnimation  및  HidingAnimation  속성이 설정되면 페이지가 로드 후에 애니메이션 효과를 확인합니다.

본문에 첨부된 Demo는 ShowingAnimation 표시효과를 Scale 페이드 인으로 설정합니다. 표시속도는 1000입니다. HidingAnimation 숨기기 효과는 explode 범(bomb)로 설정됩니다. 감추기 속도는 1000입니다.

참고 코드는 다음과 같습니다. ：

```csharp
<ShowingAnimation Duration="1000">
<Animated Effect="Scale" />
</ShowingAnimation>
<HidingAnimation Duration="1000">
<Animated Effect="explode" />
```

페이지를 추가로드하고 드롭 다운 상자를 열면 애니메이션 효과가 나타나게 됩니다. 드롭 다운 메뉴에는 각 선택 가능 옵션 항목이 나타나게 됩니다. 드롭 다운 상자를 열고 닫는 것에도 애니메이션 효과가 있습니다. 다음의 그림과 같습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc3-7-1.gif)

  

본문 Demo의 소스코드는 다음과 같습니다. :

[C1 ComboBox 애니메이션 효과 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1ComboBox-animation.zip)


## C1Editor의 HTML내용 작성과 관리

[C1Editor 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1Editor.zip)

ASP.NET의 C1Editor는 비 엔지니어 사용자가 어떤 웹 페이지에서도 HTML을 생성하고 관리할 수 있도록 합니다. 직관적이고 Microsoft Word와 유사한 편집기를 사용하여 모든 텍스트 상자와 사용자 지정 스타일을 바꿀 수 있습니다.  
본문에서는 C1Editor컨트롤을 통한 HTML 내용의 작성 관리를 소개합니다.

  

**C1Editor 추가**

C1Editor를 페이지에 추가하면 에디터가 생성됩니다. 해당 에디터는 Microsoft Office의 스타일과 기능 영역 인터페이스를 실현합니다. 이 기능 영역은 관련 명령을 일련의 탭으로 구성하여 사용자가 메뉴 계층 구조를 탐색 할 필요없이 편집기 기능을 익힐 있습니다. 코드를 참고하세요. :

```csharp
<wijmo:C1Editor runat="server" 
ID="Editor1" Width="760" Height="530"  Text="The Insert tab contains groups of commands that enable end-users to insert items, 
such as images or paragraph breaks, into the text editor. 
Underneath the Format tab are four groups – Tables, Breaks, 
Forms, and Special – that house closely related tasks. ">
</wijmo:C1Editor>
```

C1Editor의 파일내용 가져오기

txt데이터소스를 App_Data폴더에 추가합니다.

File.OpenText를 사용하여 읽을 수 있는 기존 텍스트 파일을 엽니다. 파일의 내용을 가져 오면 참조 코드는 다음과 같습니다.

```csharp
private string GetFileContent()
{
    string text = string.Empty;
    StreamReader sr = File.OpenText(Server.MapPath("~/App_Data/JavaScript.txt"));
    try
    {
        text = sr.ReadToEnd();
    }
    catch { }
    finally
    {
        sr.Close();
     }
    return text;
 }
```

페이지에서 추가 로드할 때 가져온 파일내용을 Editor.Text에 설정해줍니다. 파일내용을 C1Editor에 표시합니다. 참고 코드는 다음과 같습니다.

```csharp
Editor1.Text = GetFileContent();
```

페이지 추가 로드 후 실행하면 다음과 같이 표시됩니다. :

![](https://www.grapecity.co.kr/images/training/c1/tc3-8-1.png)

  

본문 Demo의 소스코드는 다음과 같습니다. :

[C1Editor 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1Editor.zip)