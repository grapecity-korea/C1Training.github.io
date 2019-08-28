---
title: ComponentOne for Winforms | 데이터 상호작용
keywords: ComponentOne, Winforms, FlexGrid, 필터링, 빅데이터 로딩, 데이터 폼, 간트 차트, 스케줄, 서브 시트
last_updated: Aug 08, 2019
summary: "ComponentOne for Winforms 가 제공하는 데이터 상호작용 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1win_dataInteraction.html
folder: mydoc
---


## C1FlexGrid의 강화된 조정 기능 체험: 행, 열, 유닛 셀의 자유로운 작성

ComponentOne WinForms 표 양식 컨트롤을 사용하는 FlexGrid는 많은 제작 기능을 제품에 담아 응용시스템을 자유롭게 조정할 수 있습니다. 예를 들어 열 너비 조정, 행 높이 조정, 셀프 어댑팅 최상의 열 너비, 셀프 어댑팅 최상의 행 높이로 푸시 창을 통해 선택하는 유닛 셀의 데이터, 가시화 일자 컨트롤이나 컴퓨터 컨트롤을 통해 지정한 유닛 셀의 값 등의 기능을 구현할 수 있습니다.

  

본편에서는 FlexGrid유닛 셀 유형을 어떻게 설정하는지 설명합니다. FlexGrid은 체크박스, 드롭 다운 리스트, 버튼, 마스크, 캘린더 및 자체정의 유닛 셀 유형을 지원합니다. 그리고 자유롭게 행, 열, 유닛 셀을 지원합니다.

  

### 1. 자체정의 FlexGrid의 각각 다른 데이터 유형

자체정의 FlexGrid기초유형 UITypEditor：

UITypeEditorControl가 ComboBox, IServiceProvider, IWindowsFormsEditorService의 포트를 사용하는 것은 다른 데이터유형의 기초가 됩니다. 상속관계는 다음과 같습니다. :

```csharp
#region ** UITypeEditorControl (base class for all of the controls below)
/// <summary>
/// UITypeEditorControl
/// </summary>
public class UITypeEditorControl :
    ComboBox,
    IServiceProvider,
    IWindowsFormsEditorService
{
}
#endregion
```

자체정의 FlexGrid의CheckListEditor데이터유형：

상기 UITypeEditorControl에서 파생되어 드롭 다운 가능한 체크박스 리스트를 만들 수 있습니다. 사용자는 하나 또는 여러 개를 선택할 수 있고, 임의의 구성을 선택할 수 있습니다. 그림과 같이 표시됩니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-1-1.png)

  

해당 유형의 정의는 다음의 코드와 같습니다. 구체적인 코드의 실현은 글 끝의Demo의CheckListEditor 유형을 참고할 수 있습니다.

  

```csharp
#region ** CheckListEditor
//
// CheckListEditor
// UITypeEditor that can be used to edit items in CheckedListBox control.
// Users can check any combination.
// 
public class CheckListEditor : UITypeEditor
#endregion
```

자체정의FlexGrid의FlexHyperlink데이터유형：

상기UITypeEditorControl에서 파생된 드롭 다운 가능한 체크박스 리스트에서 사용자는 하나 또는 여러 개를 선택할 수 있습니다. 결과는 다음 그림과 같습니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-1-2.png)

  

해당 유형의 정의는 다음의 코드와 같습니다. 구체적인 코드의 실현은 글 끝의 Demo의FlexHyperlink 유형을 참고할 수 있습니다.

  

### 2. 수동추가 FlexGrid 의 열 및 데이터유형

본편에서의 FlexGrid는 논 바인딩 모드입니다. 수동으로 열과 데이터를 추가해야 합니다.  
먼저 FlexGrid.Cols.Count를 통해 FlexGrid의 열의 개수를 설정합니다. Demo에는 13개가 있습니다.  
c1FlexGrid1.Cols.Count = 13 ；  
그 다음 Column의DataType을 통해 각 열의 데이터유형을 설정하고 Width속성으로 열 너비를 설정합니다.  
설정된 열의 데이터유형은 스텝1의 CheckListEditor입니다，코드는 다음을 참고합니다. ：

```csharp
//Checkbox List column
Column checkListCol = c1FlexGrid1.Cols[_checkListCol];
CheckListEditor checkListEditor = new CheckListEditor(new string[] { "덴마크어", "네덜란드어", "영어", "핀란드어", "프랑스어", "독일어", "이탈리아어", "노르웨이어", "폴란드어", "포르투갈어", "스페인어", "스웨덴어" });
checkListCol.Caption = "체크박스리스트";		
checkListCol.Editor = new UITypeEditorControl(checkListEditor, false);
checkListCol.Width = 150;
```

설정된 열의 데이터유형은 스텝1의 FlexHyperlink입니다. 코드는 다음을 참고합니다. ：

  

```csharp
//Hyperlink column
Column hyperlinkCol = c1FlexGrid1.Cols[_hyperlinkCol];

hyperlinkCol.AllowEditing = true;
hyperlinkCol.Width = 160;

hyperlinkCol.Caption = "하이퍼링크";
hyperlinkCol.ComboList = "...";				
CellStyle cs = c1FlexGrid1.Styles.Add("NewLink");
cs.Font = new Font(c1FlexGrid1.Font, FontStyle.Underline);
cs.ForeColor = Color.Blue;
cs = c1FlexGrid1.Styles.Add("OldLink");
cs.Font = new Font(c1FlexGrid1.Font, FontStyle.Underline);
cs.ForeColor = Color.Purple;
```

### 3. 수동추가 FlexGrid의 유닛 셀 데이터

[FlexGrid 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/FlexGrid_ColumnCellTypeDemo.zip)

이미 추가된 열을 바탕으로 이제 FlexGrid에 데이터를 채워주어야 합니다.  
먼저, FlexGrid.Rows.Count를 통해 행의 개수를 설정합니다. Demo에는 21개가 있습니다.  
c1FlexGrid1.Rows.Count = 21;

  

그리고 코드를 통해 데이터를 채워나갑니다. 구체적인 코드는 본문 아래에 첨부한 Demo의LoadData방법을 참고해 주시기 바랍니다.  
FlexGrid 자체정의 한 CheckListEditor열에 데이터를 채워줍니다. 코드는 다음과 같이 참고해 주시기 바랍니다. :

```csharp
string languages = "스페인어|독일어|네덜란드어, 프랑스어, 독일어|포르투갈어|영어, 프랑스어|덴마크어|핀란드어, 스웨덴어|프랑스어|독일어|영어|이탈리아어|스페인어|핀란드어, 노르웨이어|폴란드어|포르투갈어|스페인어|스웨덴어|프랑스어, 독일어, 이탈리아어|영어|영어";            
for (int i = 1; i < c1FlexGrid1.Rows.Count; i++)
{           
    //Load checkbox list data
    c1FlexGrid1[i, _checkListCol] = languages.Split('|')[i - 1];
}
```

FlexGrid 자체정의 한 FlexHyperlink 열에 데이터를 채워줍니다. 코드는 다음을 참고해 주시기 바랍니다. :

```csharp
//Load hyperlink column
c1FlexGrid1[1, _hyperlinkCol] = new FlexHyperlink("여행비서", "http://www.turismo.gov.ar/eng/menu.htm");
c1FlexGrid1[2, _hyperlinkCol] = new FlexHyperlink("오스트리아 대사관", "http://www.austria.org/");
c1FlexGrid1[3, _hyperlinkCol] = new FlexHyperlink("벨기에여행", "http://www.visitbelgium.com/");
c1FlexGrid1[4, _hyperlinkCol] = new FlexHyperlink("브라질 - 위키백과", "http://en.wikipedia.org/wiki/Brazil");
c1FlexGrid1[5, _hyperlinkCol] = new FlexHyperlink("캐나다웹사이트", "http://www.canada.com/");
c1FlexGrid1[6, _hyperlinkCol] = new FlexHyperlink("덴마크웹사이트", "http://www.denmark.dk/");
c1FlexGrid1[7, _hyperlinkCol] = new FlexHyperlink("핀란드뉴스", "http://finland.fi/");
c1FlexGrid1[8, _hyperlinkCol] = new FlexHyperlink("프랑스여행사이트", "http://www.franceguide.com/");
c1FlexGrid1[9, _hyperlinkCol] = new FlexHyperlink("독일정보사이트", "http://www.germany.info/");
c1FlexGrid1[10, _hyperlinkCol] = new FlexHyperlink("아일랜드발견", "http://www.discoverireland.ie/");
c1FlexGrid1[11, _hyperlinkCol] = new FlexHyperlink("이탈리아에 관해", "http://www.state.gov/r/pa/ei/bgn/4033.htm");
c1FlexGrid1[12, _hyperlinkCol] = new FlexHyperlink("멕시코여행", "http://www.visitmexico.com/");
c1FlexGrid1[13, _hyperlinkCol] = new FlexHyperlink("노르웨이 웹사이트", "http://www.norway.org/");
c1FlexGrid1[14, _hyperlinkCol] = new FlexHyperlink("폴란드.pl", "http://www.poland.pl/");
c1FlexGrid1[15, _hyperlinkCol] = new FlexHyperlink("포르투갈지도", "http://www.portugal-info.net/maps/");
c1FlexGrid1[16, _hyperlinkCol] = new FlexHyperlink("스페인여행자", "http://www.spain.info/");
c1FlexGrid1[17, _hyperlinkCol] = new FlexHyperlink("스웨덴여행", "http://www.visitsweden.com/");
c1FlexGrid1[18, _hyperlinkCol] = new FlexHyperlink("스위스여행", "http://www.about.ch/");
c1FlexGrid1[19, _hyperlinkCol] = new FlexHyperlink("구글영국", "http://www.google.co.uk/");
c1FlexGrid1[20, _hyperlinkCol] = new FlexHyperlink("아메리카합중국 - 위키백과", http://en.wikipedia.org/wiki/United_States);
```

이제 FlexGrid의 행, 열, 유닛 셀의 작성에 성공했습니다. 결과는 다음 그림과 같습니다. :

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-1-3.png)

  

[FlexGrid 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/FlexGrid_ColumnCellTypeDemo.zip)



## C1FlexGrid：마이닝 데이터 필터링

이번 편에서는 ComponentOne WinForms 표 양식 컨트롤을 사용하여 FlexGrid의 빅 데이터에 대한 필터링, 순서배열, 그룹 나누기, 통합, 프린트, 내보내기에 대해 설명합니다.

  

FlexGrid는 최초 필터링, 순서배열, 그룹 나누기 및 통합 등의 데이터 정리 및 마이닝 도구를 제공합니다. 사용자는 간단하게 원하는 인명이나 지역을 필터링할 수 있으며 매출액이 300만을 넘는 점포의 리스트 같은 복잡한 업무 로직을 끌어올 수도 있습니다. 또 순서배열, 그룹나누기와 통합 등을 통해 데이터의 의미가 더욱 분명하게 드러나도록 각종 KPI 데이터를 결합합니다. 이 밖에, FlexGrid는 표 양식 컨트롤이면서 보고서 기능도 제공하며, 프린트와 내보내기 기능을 통해 데이터 분석결과를 종이문서, Excel 또는 PDF파일로 출력할 수 있습니다.

  

### 1. FlexGrid 자체 정의 필터

FlexGrid는 자체정의 필터로 전문적인 수치를 처리할 수 있습니다. 이 기능은 예를 들어 자체정의 필터의 필터링 색상, 지리 또는 자체정의 데이터 유형 방면 등에 추천합니다.  
자체정의 필터를 만들려면 반드시 두 가지 유형을 만들어야 합니다. ：

• 필터：  이 유형은 IC1ColumnFilter포트를 반드시 사용해야 합니다. 필터가 특정한 값에 응용되도록 지정할 수 있습니다. 필터를 리셋하고 필터의 변수를 조사하고 편집하는데 사용되는 에디터를 회수해야 합니다.

• 필터 에디터： 이 유형은 반드시 Control로부터 이어 받아， IC1ColumnFilterEditor의 포트를 사용해야 합니다. 해당 포트는 에디터를 초기화하고 필터에 변경 응용되는 사용방법을 지정할 수 있습니다.  
자체 정의 필터의 샘플은 세 개의 자체정의필터를 포함합니다. 필터유형의 색상，일자/시간과 문자열의 값을 필터링 하는데 사용됩니다.  
본편의 Demo에서는 각각 자체정의 한 필터색상，일자와 문자열을 필터링합니다. 구체적인 코드는 Demo의 CustomFilter파일 폴더에서 찾아볼 수 있습니다.

색상필터：

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-2-1.png)

  

날짜필터：

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-2-2.png)

  

문자열필터：

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-2-3.png)

  

### 2. 데이터 소스 초기화 및 FlexGrid 필터 설정

먼저 DataTable데이터 소스를 설정합니다. 5개 열에 데이터를 추가합니다. 그 다음 FlexGrid의 DataSource를 통해 데이터 소스를 바인딩합니다. 다시 OwnerDrawCell이벤트를 통해 Cell을 그립니다. 마지막으로 FlexGrid의Column Filter에 상기 자체정의 필터를 설정해줍니다. 구체적인 코드는 다음과 같습니다. ：

```csharp
public CustomFiltering()
{
    InitializeComponent();

    //// add demo properties
    //AddProperty("AllowFiltering", _flex);

    dt.Columns.Add("문자열", typeof(String));
    dt.Columns.Add("일자", typeof(DateTime));
    dt.Columns.Add("정형", typeof(int));
    dt.Columns.Add("색상명", typeof(KnownColor));
    dt.Columns.Add("색상", typeof(Color));

    String[] names =
        {
            "Rob Walters",
            "Janice Galvin",
            "Garrett Vargas",
            "David Campbell",
            "Lynn Tsoflias",
            "Linda Mitchell",
            "Jillian Carson",
            "Alan Brewer",
            "William Vong"
        };

    var rnd = new Random();
    foreach (KnownColor kc in Enum.GetValues(typeof(KnownColor)))
    {
        Color clr = Color.FromKnownColor(kc);
        dt.Rows.Add(names[rnd.Next(0, 8)], DateTime.Today.AddDays(-rnd.Next(0, 100)), rnd.Next(0, 1000), kc, clr);
    }

    // configure grid
    _flex.DataSource = dt;
    _flex.DrawMode = C1.Win.C1FlexGrid.DrawModeEnum.OwnerDraw;
    _flex.OwnerDrawCell += _flex_OwnerDrawCell;
    _flex.AllowEditing = false;
    _flex.AllowFiltering = true;
    // assign custom filters
    _flex.Cols["색상"].Filter = new ColorFilter();
    _flex.Cols["일자"].Filter = new DateFilter();
    _flex.Cols["색상명"].Filter = new StringFilter();

}
```

### 3. FlexGrid의 Cell 다시 그리기

FlexGrid의 OwnerDrawCell이벤트를 이용하여 Cell을 다시 작성합니다. 코드는 다음과 같습니다. ：

  

```csharp
void _flex_OwnerDrawCell(object sender, C1.Win.C1FlexGrid.OwnerDrawCellEventArgs e)
{
    if (_flex[e.Row, e.Col] is Color)
    {
        var clr = (Color)_flex[e.Row, e.Col];
        if (clr != null)
        {
            e.DrawCell(C1.Win.C1FlexGrid.DrawCellFlags.Background | C1.Win.C1FlexGrid.DrawCellFlags.Border);
            var rc = e.Bounds;
            rc.Inflate(-4, -2);
            using (var br = new SolidBrush(clr))
            {
                e.Graphics.FillRectangle(br, rc);
                e.Graphics.DrawRectangle(Pens.Black, rc);
            }
        }
    }
}
```

### 4. FlexGrid의 필터, 순서배열 및 그룹 나누기 시연

상기 코드에 따라 FlexGrid는 필터를 통해 순서배열, 그룹 나누기 및 통합 등의 기능을 결합하여 각종 KPI데이터를 더욱 분명하게 나타냅니다. 결과는 다음 그림과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-2-4.png)

  

해당 유형의 정의는 다음의 코드와 같습니다. 구체적인 코드의 실현은 글 끝의 Demo의FlexHyperlink 유형을 참고할 수 있습니다.

  

### 5. FlexGrid 프린트

[FlexGrid 프린트 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/CustomFilterDemo.zip)

FlexGrid는 표 양식 컨트롤일 뿐만 아니라 사용자를 위해 보고서 기능도 제공하고 있습니다. 프린트 기능을 통해 데이터 분석결과를 프린트로 생성합니다. 이 때, FlexGrid.PrintGrid기능을 이용하면 쉽게 프린트 할 수 있습니다.

  

코드예시：

```csharp
this._flex.PrintGrid("CustomFilter", C1.Win.C1FlexGrid.PrintGridFlags.ShowPreviewDialog);
```

프린트 미리 보기 결과는 다음과 같습니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-2-5.png)

  

[FlexGrid 프린트 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/CustomFilterDemo.zip)


## C1FlexGrid 고성능 빅 데이터 로딩방법

C1FlexGrid을 사용하여 최종사용자를 위한 고성능 업무 데이터의 표시와 관리능력을 제공합니다. C1FlexGrid는 표 양식컨트롤 데이터 처리능력을 완벽하게 갖추고 있습니다. 바인딩 데이터 소스는 물론 논 바인딩 모드도 수지상 업무데이터 모드이며 고성능으로 데이터를 로딩할 수 있습니다. 100만행 × 10열 데이터 로딩은 0.27초면 가능합니다.

  

본편에서는 FlexGrid가 어떻게 빅 데이터를 로딩하는지 확인할 수 있습니다.

  

### 1. 데이터소스 정의

먼저, 10열 FlexGrid 데이터소스를 정의합니다. 코드는 다음과 같습니다. :

```csharp
public class MyItem
{
    public int ID { get; set; }
    public string 성명 { get; set; }
    public bool? 표기 { get; set; }
    public DateTime? 일자 { get; set; }
    public double? 값1 { get; set; }
    public double? 값2 { get; set; }
    public double? 값3 { get; set; }
    public double? 값4 { get; set; }
    public double? 값5 { get; set; }
    public double? 값6 { get; set; }
}
```

### 2. BackgroundWorker를 통해 FlexGrid데이터 로딩

[FlexGrid 데이터 로딩 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/FlexGrid_Performance.zip)

BackgroundWorker는 .NET에서 사용되는 다중 스레드 미션을 수행하는 컨트롤입니다. 편집자가 다중 스레드에서 단독적으로 일련의 작업을 하는 것을 허용합니다. 해당 컨트롤은 3개의 이벤트：DoWork , ProgressChanged 및 RunWorkerCompleted가 있습니다. 프로그램에서RunWorkerAsync방법을 실행하면 DoWork이벤트가 가동되어 처리하게 됩니다. 이벤트의 처리는 이벤트 처리과정 중, ReportProgress방법을 실행하면 ProgressChanged 이벤트가 가동되어 처리하게 됩니다. DoWork이벤트 처리가 마무리 되면RunWorkerCompleted이벤트가 생성됩니다.

  

FlexGrid초기화：

Command Click에서 FlexGrid데이터 소스를 없앱니다. 행렬 값을 다시 취득하여 RunWorkerAsync방법을 실행합니다. 구체적인 코드는 다음과 같습니다. ：

  

```csharp
c1Command1.Enabled = false;

// clear FlexGrid
c1FlexGrid1.DataSource = null;
c1FlexGrid1.Rows.Count = 1;
c1FlexGrid1.Cols.Count = 1;

count = (int)txtCount.Value;
progressBar.Maximum = count;

// run background worker
worker.RunWorkerAsync();
```

FlexGrid데이터 소스 준비：

프로그램 중 RunWorkerAsync방법을 실행하면 DoWork이벤트가 가동되어 처리됩니다. 해당 이벤트에서 FlexGrid가 필요한 빅 데이터를 준비합니다. 코드는 다음과 같습니다.

```csharp
for (int i = 0; i < count; i++)
{
    // report progress periodically
    if (i % 1000 == 0)
    {
        worker.ReportProgress(0, i);
    }

    MyItem m = new MyItem();
    m.ID = i;
    m.성명 = "Row" + i.ToString();
    m.표기 = i % 2 == 0 ? true : false;
    m.일자 = DateTime.Now.Add(new TimeSpan(i, i, i));
    m.값1 = (double)rnd.Next(int.MaxValue);
    m.값2 = (double)rnd.Next(int.MaxValue);
    m.값3 = (double)rnd.Next(int.MaxValue);
    m.값4 = (double)rnd.Next(int.MaxValue);
    m.값5 = (double)rnd.Next(int.MaxValue);
    m.값6 = (double)rnd.Next(int.MaxValue);
    list.Add(m);
}
```

FlexGrid데이터량 동시 표시：

DoWork이벤트 처리 과정 중, ReportProgress를 실행하면 ProgressChanged이벤트가 생성됩니다. 더 나아가 FlexGrid가 로딩한 데이터소스의 상태를 처리하고 데이터 량(행렬 개수)을 동시에 표시하게 됩니다. 코드는 다음과 같습니다.

```csharp
void worker_ProgressChanged(object sender, ProgressChangedEventArgs e)
{
	lblStatus.Text = string.Format("{0} / {1} 행", ((int)e.UserState).ToString(), count.ToString());
	lblStatus.Text = string.Format("{0} / {1} 행", ((int)e.UserState).ToString(), count.ToString());
}
```

FlexGrid데이터 소스 로딩：

DoWork이벤트 처리 종료 후, RunWorkerCompleted이벤트가 생성됩니다. 해당 이벤트 내에서 FlexGrid의 데이터 소스를 로딩하고 각 열의 데이터 유형을 작성합니다. 코드는 다음과 같습니다. :

  

```csharp
void worker_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)
{
    var items = (IList)e.Result;
    if (items.Count == 0)
    {
		MessageBox.Show("내부저장한도를 초과했습니다. 개수가 적은 항목모음으로 시도해 보세요. ");
    }
	else
    {
        try
        {
            // load flexgrid with redraw = false for best performance
            c1FlexGrid1.Redraw = false;
            c1FlexGrid1.DataSource = items;
            c1FlexGrid1.Redraw = true;

            // custom editors
            c1FlexGrid1.Cols["일자"].Editor = dateTimePicker1;
            c1FlexGrid1.Cols["값1"].Editor = numericUpDown1;
            c1FlexGrid1.Cols["값2"].Editor = numericUpDown1;
            c1FlexGrid1.Cols["값3"].Editor = numericUpDown1;
            c1FlexGrid1.Cols["값4"].Editor = numericUpDown1;
            c1FlexGrid1.Cols["값5"].Editor = numericUpDown1;
            c1FlexGrid1.Cols["값6"].Editor = numericUpDown1;
        }
	    catch (Exception)
        {
            MessageBox.Show("내부저장한도를 초과했습니다. 개수가 적은 항목모음으로 시도해 보세요.");
        }
        c1Command1.Enabled = true;
}
```

이렇게 Demo에서의FlexGrid는 기다릴 필요 없이 백만 행의 데이터를 표시할 수 있습니다. 결과는 다음 그림과 같습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-3-1.png)

  

[FlexGrid 데이터 로딩 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/FlexGrid_Performance.zip)


## C1InputPanel：데이터 폼을 빠르게 생성하는 방법

[Input Panel 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1InputPanel.zip)

본문에서는 C1InputPanel 컨트롤로 지정 데이터 소스에 근거하여 빠르게 데이터 폼을 생성하는 방법을 소개합니다. 완벽한 데이터 입력 스타일 폼으로 표현되며, 많은 구성 요소의 설계, 레이아웃, 외관 및 진행 관리를 할 수 있습니다.  
데이터 폼을 생성하는 방법은 다음과 같습니다. ：

  

### 1. C1InputPanel를 폼에 로딩

툴 상자에서 C1InputPanel 컨트롤을 직접 폼에 드래그합니다.

  

### 2. 데이터 소스 선택

DataSource속성을 통해 해당 컨트롤이 데이터 소스를 지정하게 됩니다. 자동으로 모든 필드의 입력 컨트롤을 만들어 냅니다. 모든 필드 및 상응하는 태그는 항상 정렬이 유지되고 TAB 키는 순서에 따라 자동으로 정의됩니다. 네비게이션 바도 폼에 추가될 것이고 이런 식으로 기록 열람, 새로운 기록 추가, 기록 삭제 또는 업데이트를 제공할 수 있습니다.

아래의 그림은 C1InputPanel 미션을 통해 선택한 데이터 소스를 표시한 것입니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-4-1.png)

  

### 3. 즉시 표 생성

데이터 소스 선택 후 어떤 설정 감추기도 지정되지 않은 상태라도 데이터 필드는 자동적으로 단 열거 방식에 따라 행을 정렬합니다. 본문의 Demo에서는 두 개의 C1InputPanel을 폼에 드래그합니다. 또한 각각 다른 데이터 소스를 선택합니다. 자동으로 생성되는 폼은 다음의 그림과 같습니다. :

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-4-2.png)

  

### 4. C1InputPanel 레이아웃 미세조정

C1InputPanel 레이아웃에 대한 미세조정을 할 수 있습니다.  
InputPanel의ChildSpacing 속성을 변경하면 컨트롤 사이의 내변 거리가 조정됩니다. 이러한 컨트롤 간 거리의 증가나 감소는 컨트롤이 가지런히 배열을 유지하도록 해줍니다.  
C1InputPanel의 항목 집합 에디터를 열어 InputGroupHeader를 추가하면 업무 로직과 데이터 베이스 폼에 따라 C1InputPanel이 그룹 나누기를 지정할 수 있습니다. 그리고 입력 필드를 각각 다른 유형으로 그룹 나누기합니다. InputGroupHeader.Collapsible 속성을 변경하면 최종 사용자가 실행했을 때 이런 그룹 나누기에 대해 펼치기와 접기가 가능하도록 합니다.  
C1InputPanel항목 집합 에디터는 아래 그림과 같습니다.

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-4-3.png)

  

[Input Panel 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1InputPanel.zip)


## C1GanttView：융합소프트웨어Project사용자 체험 Gantt 차트 만들기

[Gantt 차트 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1GanttView.zip)

Gantt 차트를 만들어 프로젝트를 관리하는 방법은 다음과 같습니다.

  

### 1. C1GanttView를 폼에 드래그합니다.

C1GanttView에서는 풍부한 기능의 툴 바와 Gantt 차트 패널을 제공합니다. 먼저 VisualStudio도구상자 안의 C1GanttView컨트롤을 직접 폼 속에 드래그해 넣습니다. 그리고 응용프로그램을 실행하면 즉시 완벽한 Project를 표시할 수 있습니다.

C1GanttView은 미션 패널, Gantt 차트 패널 및 완벽한 툴바를 모두 컨트롤에 집약하여 구성과 설치 작업을 줄였습니다. 툴바에 이미 모든 에디터와 팝업 창을 집약한 것도 주목할만한 점입니다. 실행 결과는 다음과 같습니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-5-1.png)

  

### 2. 에디터를 통해 적요미션, 캘린더 설정, 조건설정, 자원과 양식 결정

계속해서 C1GanttView의 설계 및 실행 시, 에디터를 통한 개발단계에서 코드가 필요 없으며 미션관리 인터페이스를 설계할 수 있습니다. 그 밖에 완성 후에도 여전히 C1GanttView에서 실제 업무에 근거하여 미션관리를 실현합니다. 적요미션, 서브미션, 작업일 설정, 사전조건, 사용한 정보 및 Gantt 차트 양식 등을 포함합니다.

  

에디터를 통해 적요미션을 정합니다. : 설계 시 에디터미션을 통해 미션 에디터를 열어 적요미션을 설정하고, 실행 시에도 미션 메시지 에디터를 열어 미션을 편집할 수 있습니다. C1GanttView 미션 메시지의 다이얼로그창은 다음과 같습니다.

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-5-2.png)

  

실행 시 적요미션 표시：  실행 시, 이미 추가한 적요 미션은 인터페이스에 표시됩니다. 사용자는 직관적으로 적요 미션을 확인하고 변경할 수 있습니다. 미션 중 아이콘이 흔들리며 미션 메시지를 표시할 수 있습니다. 구체적인 것은 아래 그림에 나타낸 것과 같습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-5-3.png)

  

Gantt 차트양식 설정：  실행 시, 최 상단의 막대형 양식 다이얼로그창을 열어 각기 다른 미션으로 양식을 설정할 수 있습니다. 다이얼로그창은 다음 그림과 같습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-5-4.png)

  

### 3. XML파일에 가져오고 내보내기

마지막으로 내보내기 기능은 제작을 마친 프로젝트관리 계획을 파일로 저장한 후 분배하거나 전달합니다.

본문 Demo 중, C1GanttView1.LoadXml방법을 사용하여 XML문서파일을 들여옵니다. 이렇게 직접 사용할 수 있습니다. 변경할 곳이 있는 경우 위의 방법 1과 방법 2에 따라 변경합니다. 들여 오기한 XML문서파일의 오버로딩 방법은 다음과 같습니다. :

```csharp
    // 적요:
    //     Loads the contents of C1.Win.C1GanttView.C1GanttView from a System.IO.Stream.
    public void LoadXml(Stream stream);
    //
    // 적요:
    //     Loads the contents of C1.Win.C1GanttView.C1GanttView from an XML file.
    public void LoadXml(string fileName);
    //
    // 적요:
    //     Loads the contents of C1.Win.C1GanttView.C1GanttView from an System.Xml.XmlDocument.
    public void LoadXml(XmlDocument doc);
```

이렇게 특수한 경우에 최종사용자가 직접 C1GanttView를 통해 가장 적합한 업무 사항의 Gantt 차트를 정할 수 있고 기타 사용자에게 제출하거나 발표하여 동시에 실행할 수 있습니다. C1GanttView를 열고 그대로 삽입한 저장버튼을 클릭하면 설계된 프로젝트 계획 및 Gantt 차트를 모두 XML문서로 저장할 수 있습니다. 저장된 XML 파일이 열린 다이얼로그창은 다음과 같습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-5-5.png)

이제 완벽한 Gantt 차트가 완성되었습니다. 본문 Demo의 소스코드는 다음과 같습니다.

[Gantt 차트 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1GanttView.zip)


## C1Schedule：스케줄 관리용 응용프로그램 개발

[C1 Schedule 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1Schedule.zip)

본문에서는 C1Schedule컨트롤을 어떻게 사용하는지 설명합니다. 간단한 스케줄 관리용 응용 프로그램을 개발하여 Outlook스타일로 사용자 체험 스케줄 표를 나타냅니다. 이 스케줄 관리 솔루션은 5개의 내장된 스케줄 및 정기적인 약속 관리 기능 등도 갖추고 있습니다.

  

### 1. 도구상자의 컨트롤을 창에 드래그

Visual Studio도구상자의 C1Schedule와C1Calendar컨트롤을 직접 창에 드래그합니다. 일반적으로 사용되는 좌우 배치로 배치한 후, 응용프로그램을 실행하면 즉시 Outlook 스타일의 사용자 체험 스케줄 표가 사용자 앞에 나타납니다. 결과는 다음 그림과 같습니다. :

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-1.png)

  

### 2. 내장된 약속관리 다이얼로그창 팝업

첫 번째 방법을 완성한 후, 실행 시, 시간 별 구간 내에서 마우스를 더블 클릭하면 “약속” 다이얼로그창이 팝업 됩니다. 또는 사용자가 직접 Enter키를 누르면 간단하게 새로운 약속을 만들거나 기존 약속을 편집할 수 있습니다. 약속은 일회성이며 스케줄 시간 내에 여러 번 중복되게 할 수도 있습니다. 알람을 설정하여 어떤 약속이라도 놓치지 않게 할 수 있습니다.  
약속 다이얼로그창은 다음 그림과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-2.png)

  

### 3. C1 스케쥴을 설정합니다.

C1Schedule 컨트롤은 C1Schedule.ViewType 속성을 사용하여 일, 주, 주중, 월별 또는 타임 라인보기 별로 일정을 볼 수 있는 5 가지 기본 제공보기를 제공합니다. 이 속성의 열거 형은 다음과 같습니다.：

```csharp
// 적요:
//     Determines the type of view to display in the C1.Win.C1Schedule.C1Schedule
//     control.
public enum ScheduleViewEnum
{
    // 적요:
    //     Day view.
    DayView = 0,
    //
    // 적요:
    //     Work week view.
    WorkWeekView = 1,
    //
    // 적요:
    //     Week view.
    WeekView = 2,
    //
    // 적요:
    //     Month view.
    MonthView = 3,
    //
    // 적요:
    //     Time Line view.
    TimeLineView = 4,
}
```

VeiwType을 사용하여 다른 열거 형 값을 설정하면 다른 뷰 효과를 얻을 수 있습니다.

  

일일 설정：  코드와 결과는 다음과 같습니다.

  

```csharp
// Switch to the DayView.
this.c1Schedule1.ViewType = ScheduleViewEnum.DayView;
```

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-3.png)

  

주간 설정 ：  코드와 결과는 다음과 같습니다.

```csharp
// Switch to the WeekView.
this.c1Schedule1.ViewType = ScheduleViewEnum.WeekView;
```

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-4.png)

  

근무주간 설정：  코드와 결과는 다음과 같습니다.

```csharp
// Switch to the WorkWeekView.
this.c1Schedule1.ViewType = ScheduleViewEnum.WorkWeekView;
```

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-5.png)

  

근무 월간 설정：  코드와 결과는 다음과 같습니다.

```csharp
// Switch to the MonthView.
this.c1Schedule1.ViewType = ScheduleViewEnum.MonthView;
```

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-6.png)

  

타임라인 설정：  코드와 결과는 다음과 같습니다.

```csharp
// Switch to the TimeLineView.
this.c1Schedule1.ViewType = ScheduleViewEnum.TimeLineView;
```

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-7.png)

  

### 4. C1Calendar와 C1Schedule 동시 설정

C1Calendar1.Schedule 속성을 설정하여 C1Calendar 및 C1Schedule 컨트롤을 함께 동기화 할 수 있습니다. 동기화 후에는 날짜를 선택하거나 지역을 선택하고 C1Schedule은 선택 항목에 따라 시간 범위 내의 모든 약속을 표시하고 지역에 대해 하루 또는 주 또는 월의 요일보기를 지정할 수 있습니다. C1Calendar 컨트롤은 사용 가능한 공간에 따라 한 번에 한 달 이상 표시 할 수 있습니다. C1Calendar의 동기화 설정된 C1Schedule코드는 다음과 같습니다. ：

```csharp
this.c1Calendar1.Schedule = this.c1Schedule1;
```

동기화 결과는 다음과 같습니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-6-8.png)

  

본문Demo의 소스코드는 다음과 같습니다. ：

  

[C1 Schedule 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/C1Schedule.zip)


## C1TrueDBGrid시트 컨트롤을 사용하여 서브 시트 만들기

[C1 서브 시트 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/TrueDBGrid-ChildGrids.zip)

본문은 C1TrueDBGrid를 사용하여 빠르게 서브시트를 만드는 방법을 소개하여 사용자가 원하는 데이터와 인터페이스를 표시할 수 있도록 합니다.

  

서브시트

True DBGrid 데이터 간에 주 관계나 서브 관계를 표시하는 것을 허용합니다. 즉, 서브 데이터는 메인 시트 안의 새로운 True DBGrid에 기록되고 사용할 수 있습니다. 간단한 ChildGrid 속성 설정을 통해 두 개의 시트 컨트롤과 몇 행의 코드를 함께 연결시킵니다. 이렇게 하면 완전히 편집 가능하도록 만들 수 있습니다. 간단한 클릭으로 메인 시트의 드롭 다운 서브 데이터가 나타나게 됩니다. True DBGrid컨트롤이 처리 가능한 단계에는 수량 제한이 없습니다.  
본문 Demo의 TrueDBGrid는 3단계 구조로 되어 있습니다. 방법은 다음과 같습니다.

  

1. TrueDBGrid 데이터 소스 연결：  각기 다른 세 개의 TrueDBGrid를 만들고 DataSource 속성을 통해 각각 데이터 소스에 연결합니다. 코드는 다음과 같습니다.

```csharp
private C1.Win.C1TrueDBGrid.C1TrueDBGrid c1TrueDBGrid1 = new C1.Win.C1TrueDBGrid.C1TrueDBGrid();
private C1.Win.C1TrueDBGrid.C1TrueDBGrid c1TrueDBGrid2 = new C1.Win.C1TrueDBGrid.C1TrueDBGrid();
private C1.Win.C1TrueDBGrid.C1TrueDBGrid c1TrueDBGrid3 = new C1.Win.C1TrueDBGrid.C1TrueDBGrid();
this.c1TrueDBGrid1.DataSource = this.customersBindingSource;
this.c1TrueDBGrid2.DataSource = this.customersOrdersBindingSource;
this.c1TrueDBGrid3.DataSource = this.ordersOrderDetailsBindingSource;
```

2. TrueDBGrid 종속관계 만들기： 각기 다른 TrueDBGrid를 메인 관계 또는 서브관계로 만듭니다. 간단한 ChildGrid속성 설정을 통해 두 개의 시트 컨트롤을 몇 행의 코드를 이용해 연결시킵니다. 예를 들어 본문의 3개의 TrueDBGrid는 c1TrueDBGrid2가 c1TrueDBGrid1의 서브관계임을 나타내고 서브 데이터를 c1TrueDBGrid1 내의 c1TrueDBGrid2에 기록합니다. 그리고 c1TrueDBGrid1의ChildGrid속성을 설정합니다. 본문의 3개의 TrueDBGrid의 종속관계설정은 다음의 코드와 같습니다. :

  

```csharp
this.c1TrueDBGrid1.ChildGrid = this.c1TrueDBGrid2;
this.c1TrueDBGrid2.ChildGrid = this.c1TrueDBGrid3;
```

이렇게 하면 완전히 편집 가능한 시트를 만들 수 있습니다. 사용자가 실행 버튼을 클릭하면 메인 시트의 드롭 다운 서브 데이터가 표시됩니다. 실행 결과는 다음 그림과 같습니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc_winforms3-7-1.png)

  

본문 Demo의 코드는 다음과 같습니다. :

  

[C1 서브 시트 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1Winforms/TrueDBGrid-ChildGrids.zip)

